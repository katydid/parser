# Hint

Calling the `Next` method returns the `Hint`.

```
Next : () -> (Hint | error | EOF)
```

The `Hint` provides a hint about the next token in [the parse tree](./tree.md).
The `Hint` is used to decide whether to `Skip`, parse the `Token` or move onto the `Next` element.

In some implementation languages, `Hint` can be indicated with a single byte or ascii character:

* '{': Open
* '}': Close
* 'k': Key
* 'v': Value

In other languages a sum type/enum is preferred to represent `Hint`.

## Hint

**TODO**

Our pull based parser would see every:

* `Node v []` as a value and return a `Hint` = `v`
* `Node k [Node v []]` as a value and return a `Hint` = `k` and Next a `Hint = v`.
* Otherwise `Node k children` as a key and return a `Hint` = `k` with `Hint`s `{` and `}` surrounding the list of children.

Also Note: at the top (start) we start with a list of trees. These are not surrounded by `Hint`s `{` and `}`.

## Why Next returns a Hint and not a Token

tl;dr: performance

The `Next` method returns a hint.

```
Next : () -> (Hint | error | EOF)
```

Using this `Hint` the user can decide to `Skip` or parse the `Token`.
Only the `Token` method will parse the actual key or value:

```
Token: () -> ((Kind, value) | error)
```

The question is why would we want to separate this two methods and not just have a single `NextToken` method:

```
Token: () -> ((Kind, value) | error | EOF)
```

The answer is CPU and memory efficiency.
We want the user to have as much control as possible over what actually gets parsed.
This way the user can efficient call `Skip` or `Next` to skip over what does not need parsing.

Note that tokenizing can be especially expensive as it can result in allocating memory, 
for example when unquoting a JSON string.
This means we should only tokenize values the user really cares about.

The reason performance is important is that in validation languages that are optimized properly the parser becomes the bottleneck.
When applying a validator as a filter through millions of record of serialized data, we want to have good reasons for being the bottleneck.

## Why not Lists of Lists, like Lisp

**TODO**

An alternative would be to model everything as a list, like Lisp does.

This would mean that an object:

```json
{"a": 1, "b": [1,2,3]}
```

would be modeled as:

```json
[["a", 1], ["b", [1,2,3]]]
```

This is a trade-off, since in this case key value are a level deeper, so slightly negatively impacted,
while in our design, the list valueas are one level deeper, which means lists are slightly negatively impacted.
In one case maps are first class and lists are second class citizens and on the other hand lists are first class and maps are second class.

We are dealing with serialized data, which is usually encoded as some type of structure or key-value pairs,
which is why we prefer to have first class key-value pairs over and second class lists.

## Why not both Lists and Maps

The second design of the parser included `Hint`s for both lists and key-value pairs:

* '[': List Opened
* ']': List Closed
* '{': Map Opened
* '}': Map Closed
* 'k': Map Key
* 'v': Map Value or List Element, that is not an Object or List.

**TODO**

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
        Node Null [
            Node (Int64 2) []
        ],
        Node Null [
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

Remember every `Node v []` would parse as a `Hint`: `v`,
while every `Node k children`, where `children != []`, would parse as a `Hint`: `k` with `{` and `}` `Hint`s surrounding the list of children.

This means our pull-based parser would parse it as:
```
{"a": 1, "b": {null: 2, null: {"c": 3, "d": 4}}}
```

Or more verbosely:
```
Next -> '{'
Next -> 'k'
Token -> '"', "a"
Next -> 'v'
Token -> '-', 1
Next -> 'k'
Token -> '"', "b"
Next -> '{'
Next -> 'k'
Token -> '_'
Next -> 'v'
Token -> '-', 2
Next -> 'k'
Token -> '_'
Next -> '{'
Next -> 'k'
Token -> '"', "c"
Next -> 'v'
Token -> '-', 3
Next -> 'k'
Token -> '"', d
Next -> 'v'
Token -> '-', 4
Next -> '}'
Next -> '}'
```

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

Given this representation our pull-based parser would parse it as:
```
{"A": {"B": "C", "D", "B": "F"}}
```

Or more verbosely:
```
Next -> '{'
Next -> 'k'
Token -> '"', "A"
Next -> '{'
Next -> 'k'
Token -> '"', "B"
Next -> 'v'
Token -> '"', "C"

Next -> 'v'
Token -> '"', "D"

Next -> 'k'
Token -> '"', "E"
Next -> 'v'
Token -> '"', "F"
Next -> '}'
Next -> '}'
```

Notice how "D" is returned as a value `v` in between the list of keys, since it as an `Node (String "D") []`.
