# Hint

The `Hint` provides a hint about the location in the structure.

We conducted a [survey of the most common serialization formats](./survey/Readme.md) and found that all the compound types can be represented as key-value pairs.

This results in only a limited amount of hints that are required for the user to know if it wants to `Skip`, parse the `Token` or move onto the `Next` element.
In some implementation languages, `Hint` can be indicated with a single byte or ascii character:

* '{': Open
* '}': Close
* 'k': Key
* 'v': Value

In other languages a sum type/enum is preferred to represent `Hint`.

## Survey

We did a [survey](./survey/Readme.md) and found that the following common compound types:

* Void
* List
* Set
* Union
* Object
* Map
* Pair (YAML only)

Each of these can be mapped to key-value pairs.

* Void is mapped to an empty key-values pairs represented as the following tokens: '{', '}'.
* A List is mapped to key-value pairs, where each key is the null value and each value is the value of the element in the list. We provide an example below.
* A Set is mapped the same as a List.
* A Union is mapped to a key and value pair, where the key represents the tag. If the union is not a tagged union, then the value is represented as just a value and not as a non compound type.
* A Map is mapped to key-value pairs, in the obvious way.
* An Object is mapped to key-value pairs, where fields are keys.
* Pair is mapped the same as a List of length two. It is not mapped to a key-value pair, since a key cannot represent a compound types.

Here we provide an example of how a list is mapped to key-value pairs.

Given the JSON list:
```json
[1,"b",{"a": 3}]
```

It will be parsed the same as if it was the following JSON:
```json
{null: 1, null: "b", null: {"a": 3}}
```

Note the keys are not gauranteed to be unique.

## Why Next returns a Hint and not a Token

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

There are two reasons:
1. We want to keep the validator language simple and as close to regular expressions as possible.
2. We want other algorithms that use the parser interface to be as simple as possible.

### Regex based Validator Language

The validator algorithm is derived from the derivative algorithm for regular expressions.

As a foundation we have the following operators:

* EmptySet
* EmptyString
* Char (replace with Key-Value Pair)
* Or
* Concat
* Star (Zero or More)

We try to keep as close as possible to the original derivative algorithm, except for replacing the Char operator.
All other operators are borrowed exactly from regular expressions.

The new operator is a Tree operator, which has a pattern for the Key and an expression (based on Regular expression) for the value:

```haskell
data Expr =
| EmptySet
| Empty
| Tree KeyPattern Expr
| Or Expr Expr
| Concat Expr Expr
| Star Expr
```

If we want a pattern that matches:
```json
{"a": 1, "b": 2}
```

We can write:
```haskell
(Tree (KeyStr "a") (Tree (KeyInt 1) Empty)) `Concat` (Tree (KeyStr "b") (Tree (KeyInt 2) Empty))
```

If we need to support lists, we need to add a new operator without a KeyPattern.
For argument sake, let us call that `Elem`.

Given the following JSON:
```json
[1, 2]
```

We can validate it with:
```haskell
(Elem (Tree (KeyInt 1) Empty)) `Concat` (Elem (Tree (KeyInt 2) Empty))
```

Given the following JSON:
```json
{1: [], 2: []}
```

We can validate it with something very similar:
```haskell
(Tree (KeyInt 1) Empty) `Concat` (Tree (KeyInt 2) Empty)
```

For these expressions to mean different things,
our validation algorithm would need to keep track of whether the parser was in an object or a list,
which would complicate the validation algorithm.

Another problem is how would you distinguish between: `{"a": [1]}` and `{"a": 1}`.

### More Complex Algorithms

The more dynamic the structure the more complex the algorithms that run out them need to be.

For example if we want to calculate the length of rather the number of elements in a structure.

If we have both maps and lists, we need to write the following code:

```go
length := 0
hint, err := parser.Next()
if err != nil {
    return length, err
}
if hint != '{' && hint != '[' {
    return length, errors.New("expected open array or map")
}
close := '}'
if hint == '[' {
    close = ']'
}
for {
    hint, err := parser.Next()
    if err != nil {
        return length, err
    }
    if hint == close {
        return length, nil
    }
    switch hint {
    case '}', ']':
        return 0, errors.New("unexpected close")
    case '[', '{', 'k':
        parser.Skip()
        length++
    case 'v':
        length++
    }
}
```

If we only have key-value pairs, then we can write:

```go
length := 0
hint, err := parser.Next()
if err != nil {
    return length, err
}
if hint != '{' {
    return length, errors.New("expected open")
}
for {
    hint, err := parser.Next()
    if err != nil {
        return length, err
    }
    if hint == '}' {
        return length, nil
    }
    if hint != 'k' {
        return 0, errors.New("expected key")
    }
    parser.Skip()
    length++
}
```

## Why are indexes represented as null

Given the JSON list:
```json
[1,"b",{"a": 3}]
```

It will be parsed the same as if it was the following JSON:
```json
{null: 1, null: "b", null: {"a": 3}}
```

But why `null` and not an index:
```json
{0: 1, 1: "b", 2: {"a": 3}}
```

It is possible to write a parser that does this manipulation.

For example when parsing:
```json
[1,"b",["a", 3]]
```
We need to keep track of two indices at a time:
```json
{0: 1, 1: "b", 2: {0: "a", 1: 3}}
```

This means that it requires an extra stack to keep track of indexes for various arrays.
This is requires a small amount of extra memory and performance to keep track of the index.

The question is what do we gain?

In case of a validator, there is no reason to validate the index of a specific element of a list.

This parser has not been used in other use cases, but until then we have no reason to undergo this expense.