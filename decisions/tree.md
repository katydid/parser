# Tree

Our parser is a pull-based parser, but the parse tree still needs an underlying model of what we imagine the parse tree would look like, if we would parse it fully into memory.

We have based our model on [Haskell's Data.Tree](https://hackage-content.haskell.org/package/containers-0.8/docs/src/Data.Tree.html#Tree).

## Haskell Data.Tree

The [Haskell Data.Tree](https://hackage-content.haskell.org/package/containers-0.8/docs/src/Data.Tree.html#Tree) type is defined as:

```haskell
data Tree a = Node {
    rootLabel :: a,         -- ^ label value
    subForest :: [Tree a]   -- ^ zero or more child trees
}
```

*Note: Sometimes we will refer to the `rootLabel` as the `label` or `field` and refer to the `subForest` as `children` going forward.*

The generic parameter `a` is mapped to a `Token`:

```elm
type Token =
  | Void -- '_' (also Null or Unit)
  | Elem -- 'i' (a list element)
  | False -- 'f'
  | True -- 't'
  | Bytes Bytes -- 'x'
  | String String -- '"'
  | Int64 Int64 -- '-' (-1 * 2^63 ... 2^63 - 1)
  | Float64 Float64 -- '.' (IEEE-754)
  | Decimal String -- '/' (ISO 6093)
  | Nanoseconds Int64 -- '9' (used for duration and time since the epoch)
  | DateTime String -- 'z' (RFC3339)
  | Tag String '#'
```

This means that our parse tree can be thought of as a type: `Tree Token`.

## Survey

We conducted a [survey of the most common serialization formats](./survey/Readme.md) and found that all the compound types can be represented as trees.

The survey found that the following common compound types:

* Object
* Map
* Void
* Union
* List
* Set
* Pair (YAML only)

Each of these can be mapped to a tree.

## Object

An Object is mapped to a tree, where each field name is a node: `Node (String fieldname) value`.
If the `value` is a single value it is mapped to a singleton list of children `[Node value []]`.
If the value is a object it is mapped to a list of fields.

For example:
```
{
    A: 1,
    B: {
        C: 2,
        D: 3,
    }
}
```

is mapped to the following tree:
```haskell
[
    Node (String "A") [Node (Int64 1) []],
    Node (String "B") [
        Node (String "C") [Node (Int64 2) []],
        Node (String "D") [Node (Int64 3) []],
    ]
]
```

## Map

A Map is the generalization of an Object.
Fieldnames are called keys and they unlike fieldnames, keys are not all of type string.
Each key-value pair is mapped to `Node key value`.

For example:
```
{
    1: "A",
    2: {
        "C": 2,
        "D": 3,
    }
}
```

is mapped to the following tree:
```haskell
[
    Node (Int64 1) [Node (String "A") []],
    Node (Int64 2) [
        Node (String "C") [Node (Int64 2) []],
        Node (String "D") [Node (Int64 3) []],
    ]
]
```

## Void

Void, null and Unit are represented as `Node Void []`.

## Union

There are two types of unions:
* Tagged Unions
* Untagged Unions

A tagged union can be one of several values, but includes a tag to let you know which value was chosen.
One common known tagged union is `Result`, where the result value can a successful result value or an error.
If both the success value and the error is represented as a string, it isn't easy to tell which is which without a tag.
Tagged unions are represented as `Node tag value`.

For example:
```
Result.Ok "success"
```

is mapped to a tree:
```
Node (String "Ok") [Node (String "success") []]
```

while a:
```
Result.Err "404"
```

is mapped to a tree:
```
Node (String "Err") [Node (String "404) []]
```

An untagged union is just a value and is represented as the underlying value.

For example, if union is an integer or string and the value is a string
```
"abc"
```

it is mapped to a tree:
```
Node (String "abc") []
```

## List

A List's elements are eached indexed with a `Node Elem [element]`.

Here we provide an example of how a list is mapped to a tree.

Given the JSON list:
```json
[1,"b",{"a": 3}]
```

it maps to the following tree:
```
[
    Node Elem [Node (Int64 1) []],
    Node Elem [Node (String "b") []],
    Node Elem [
        Node (String "a") [
            Node (Int64 3) []
        ]
    ]
]
```

Prior art for this representation (wrapping each element in a node) can be found in [XML-RPC](https://en.wikipedia.org/wiki/XML-RPC), where an array is represented as a list of values:

```xml
<array>
  <data>
    <value><i4>1404</i4></value>
    <value><string>Something here</string></value>
    <value><i4>1</i4></value>
  </data>
</array>
```

### Why does Elem exist

We chose to introduce a new `Kind`: `Elem`, instead of reusing `Void` to avoid confusion.

Without `Elem` the following JSON:
```json
[1,"b",{"a": 3}, {"c": 4}]
[1,"b",{"a": 3, "c": 4}]
```

would both map to the following tree:
```haskell
[
    Node (Int64 1) [],
    Node (String "b") [],
    Node (String "a") [
        Node (Int64 3) []
    ],
    Node (String "c") [
        Node (Int64 4) []
    ]
]
```

This will make validation impossible for some use cases.

For example:

If we only want to find people with a moving date in the first half of the year in the last 10 years.

The person, does not have a moving date in the last 10 years in the first half of the year, but they do have on in 1985:
```json
{"Moving Dates": [{"Month": 7, "Year": 2022}, {"Year": 1985, "Month": 4}, {"Year": 2020, "Month": 8}]}
```

If we cannot distinguish between these pairs being in different structures using some index, then we just have a list of months and years:

```haskell
[   
    Node (String "Moving Dates") [
        Node (String "Month") [Node (Int64 7) []],
        Node (String "Year") [Node (Int64 2022) []],
        Node (String "Year") [Node (Int64 1985) []],
        Node (String "Month") [Node (Int64 4) []],
        Node (String "Year") [Node (Int64 2020) []],
        Node (String "Month") [Node (Int64 8) []],
    ]
]
```

Given this list we will get a false positive using a validator.

### Why not proper indexes instead of Elem

Why Elem and not an index:
```
[
    Node (Int64 0) [Node (Int64 1) []],
    Node (Int64 1) [Node (String "b") []],
    Node (Int64 2) [
        Node (String "a") [
            Node (Int64 3) []
        ]
    ]
]
```

It is possible to write a parser that does this augmentation.

For example, when parsing:
```json
[1,"b",["a", 3]]
```

the augmenter needs to keep track of two indices at a time:
```
[
    Node (Int64 0) [Node (Int64 1) []],
    Node (Int64 1) [Node (String "b") []],
    Node (Int64 2) [
        Node (Int64 0) [Node (String "a") []],
        Node (Int64 1) [Node (Int64 3) []]
    ]
]
```

This means that it requires an extra stack to keep track of indexes for various arrays.
This is requires a small amount of extra memory and performance to keep track of the index.
We do not want the default parser to include this extra cost.

We cannot see what we would gain for this extra cost.
In case of a validator, there is no reason to validate the index of a specific element of a list.
This parser has not been used in other use cases, but until then we have no reason to undergo this expense.
If we do find there is this extra expense, we could create an augmenter to rather keep track of the index.

## Set

A Set is mapped to the same tree as a list.
We do not need to worry about the items in the set being unique as that will be the problem of the serializer, not the parser.

## Pair

Out of all the serialization formats we surveyed, only YAML supports a pair.
We can't gaurantee that the first element in the pair is a type that can be represented in a Node's label and since the Pair type is so rare, we err on the side of generality rather than conciseness and represent a pair as list of two elements.

The pair:
```
(a, b)
```

is mapped to a tree:

```haskell
[
    Node Elem [Node (String "a") []],
    Node Elem [Node (String "b") []]
]
```

## Why Haskell's Data.Tree

Why choose a model for a tree based on a Haskell data structure for a tree?

The Katydid validator algorithm is based on Brzozowski's derivatives for regular expressions on strings.
The Haskell data structure for a tree has a very close relationship to strings, which makes it a good fit for the validator algorithm.

If we squint a list of trees is just a string, where each label is a character and each tree has no children.
For example, we can encode the string "abc" as a list of trees also known as a forest:

```haskell
[Node 'a' [], Node 'b' [], Node 'c' []]
```

What is even better is that each Node encodes its children as a list of trees or `subForest`.
This means we can apply the derivative algorithm recursively on the `subForest` or children of each `Node`.

## Why not a binary tree, instead of a list of children.

We can represent a list as a binary tree.

For example, given a string "abcd" represented as a list:
```
Cons 'a' (Cons 'b' (Cons 'c' (Cons 'd' Nil)))
```

We can convert the list to a binary tree, with binarization:
```
Bin (Val 'a') (Bin (Val 'b') (Bin (Val 'c') (Val 'd')))
```

The values are assigned to the left nodes and the continuation of the list to the right node, until the last value, which is also assigned to the right node.
This way we can convert all lists to trees.

We can also convert a binary tree to a list.
We just need to pick an order of traversal, in-order, pre-order or post-order.

This will work, but it seems convoluted, given our derivative algorithm is built to run on lists, why wouldn't we just use a list.

## Example: Parsing JSON

We can imagine JSON would parse into our tree.

Given the following JSON:
```json
{"a": 1, "b": [2, {"c:" 3, "d": 4}]}
```

It would parse into our parse tree as:
```haskell
[
    Node (String "a") [
        Node (Int64 1) []
    ],
    Node (String "b") [
        Node Elem [
            Node (Int64 2) []
        ],
        Node Elem [
            Node (String "c") [
                Node (Int64 3) []
            ],
            Node (String "d") [
                Node (Int64 4) []
            ]
        ]
    ]
]
```

Notice that if we didn't add `Node Elem` then we wouldn't be able to tell that `2` and `"c"` are not elements of the same list.

## Example: Parsing XML

The following XML:
```xml
<A><B>C</B>D<B>F</B></A>
```

can be presented as a Tree:
```haskell
[
    Node (String "A") [  
        Node (String "B") [
            Node (String "C") []
        ],
        Node (String "D") [],
        Node (String "B") [
            Node (String "F") []
        ]
    ]
]
```

We could have modeled XML as a list, with `Void` fields, but that would be overly verbose.

We could also have given "D" a `Void` child: `Node (String "D") [Node Void []]`, so that it was a consistent list of field value pairs, but this would require some foresight.
For example, if we parsed `<A>D<B>C</B></A>`, we cannot know that "D" needs to be a value of a field, before we saw the "B".

It would be up to the specific parse implementation to decide how to represent `<D/>` as Tree, but we would also propose `Node (String "D") []`, since it has no children.
In cases where it is necessary to also include the information whether the node is a text node or an element, we propose using custom [tags](./tags.md).

## Why not key-value pairs

Given the XML example:
```xml
<A><B>C</B>D<B>F</B></A>
```

That parses into the tree:
```haskell
[
    Node (String "A") [  
        Node (String "B") [
            Node (String "C") []
        ],
        Node (String "D") [],
        Node (String "B") [
            Node (String "F") []
        ]
    ]
]
```

It shows that there is a key without a value, which is really just a value.
The list of key-value pairs, does not offer this flexibility.

We could attempt represent it as key-value pairs:
```
{A: {B: C, D: {}, B: F}}
```
But now `C` and `D` are treated inconsistently.

We could treat them consistently:
```
{A: {B: {C: {}}, D: {}, B: {F: {}}}}
```

If we do this, it is exactly the same as the Haskell Data.Tree,
except we have to explain that keys can be duplicates, which can be confusing to some.

## Why not Lists of Lists, like Lisp

An alternative would be to model everything as a list, like Lisp does.

This would mean that an object:

```json
{"a": 1, "b": [1,2,3]}
```

would be modeled as:

```json
[["a", 1], ["b", [1,2,3]]]
```

This is a trade-off, since in this case the labels ("a", "b") are a level deeper, which means they are slightly negatively impacted.
In our design, the list values are one level deeper, which means lists are slightly negatively impacted.
In one case labels are first class and lists are second class citizens and on the other hand lists are first class and labels are second class.

We are dealing with serialized data, which is usually encoded as some type of structure or field-value pairs,
which is why we prefer to have first class fields over and second class lists.

## Why not both Lists and Maps

The second design of the parser included `Hint`s for both lists and maps:

* '[': List Opened
* ']': List Closed
* '{': Map Opened
* '}': Map Closed
* 'k': Map Key
* 'v': Map Value or List Element, that is not a Map or List, but just a basic value.

**TODO**
