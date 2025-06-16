# Parser

The Katydid Parser is a generic interface created to be implemented for many serialization formats in a variety of programming languages.

Our main use case is so that one schema language (for example, JSONSchema, but not limited to) can be applied to any serialization format.
We will use JSON and XML in most examples, but this interface also supports Protobufs and other binary formats.

## Interface

We describe the interface in a language agnostic way, so that this can be used by for implementing a parser for any serialization in almost any programming language.
We found that [most serialization formats are Sequential](./decisions/survey/comparison.md) and have decided on an interface with three methods:

* Next
* Skip
* Token

This interface has 3 methods. They take zero parameters, except for the parser's internal state, which they need to update.
If you are implementing this in a functional language without monads, please remember to add the state as an extra parameter and result.

## Errors

When we mention "returns a value or an error", this should be represented in the most efficient way specific to that programming language.
A language supporting tagged unions/sum types/enums/optional/maybe should consider using them, but if this allocates memory on the heap, a more efficient structure could be used.
Other options include: tuples, unions, multiple return parameters or throwing a checked exception (instead of returning an error).

When we mention "returns an error or EOF", this could be represented as just an error, if there is a way to distinguish between a general error and an error that is an "end of file".

### Next

The `Next` method, returns a `Hint`, an error or an `EOF`, when no more tokens are left:

```
Next : () -> (Hint | error | EOF)
```

The `Next` method does as little work as possible to move onto the next token and to provide a hint about the kind of token is next.

### Hint

The `Hint` provides a hint about the location in the structure.

We conducted a [survey of of the most common serialization formats](./decisions/survey/Readme.md) and found that a limited amount of [Compound](./compound.md) types need to be supported:

* Map
* List

This results in only a limited amount of hints that are required for the user to know if it wants to `Skip`, parse the `Token` or move onto the `Next` element.

In some implementation languages, `Hint` can be indicated with a single byte or ascii character:

* '[': List Opened
* ']': List Closed
* '{': Map Opened
* '}': Map Closed
* 'k': Map Key
* 'v': Map Value or List Element, that is not an Object or List.

In other languages a sum type/enum is preferred to represent `Hint`.

### Skip

The `Skip` method possibly returns an error or EOF:

```
Skip : () -> (error | EOF)?
```

The `Skip` method allows the user to skip over uninteresting parts of the parse tree.
Based on the `Hint` skip has different intuitive behaviours. 
If the `Hint` was:

* '{': the whole `Map` is skipped.
* 'k': the key's value is skipped.
* '[': the whole `List` is skipped.
* 'v': the rest of the `Map` or `List` is skipped.
* ']': same as calling `Next` and ignoring the `Hint`.
* '}': same as calling `Next` and ignoring the `Hint`.

### Kind

The `Kind` represents the `kind` of the value.

We conducted a [survey of of the most common serialization formats](./decisions/survey/Readme.md) and found that a limited amount of [Scalar](./scalar.md) types need to be supported.
We represent these with a specific `Kind`:

* '_': Null
* 't': True
* 'f': False
* 'x': Bytes (Bytes)
* '"': String (String)
* '-': Int64 (Int64)
* '.': Float64 (Float64)
* '/': Decimal (String)
* '9': Nanoseconds (Int64) (used for duration and time)
* 'T': Date Time ISO 8601 (String)
* '#': Custom Tag (String)

Your implementation language will probably need these basic types:

* `Bytes`
* `String`
* `Int64`
* `Float64`

### Token

The `Token` method returns a `Kind`, value or an error.

```
Token: () -> ((Kind, value) | error)
```

The `Token` method is the only method that returns the value of a token.
The `Token` method's design varies dependending on implementation language and some experimentation is still required.
We will give some examples.

In a dynamically typed language the above description of the `Token` method is sufficient.

In a language with sum types, we recommend declaring `Token` as a sum type and not using `Kind`:
```
GetToken : () -> (Token | error)

type Token =
  | Null
  | False
  | True
  | Bytes bytes
  | String string
  | Int64 int64
  | Float64 float64
  | Decimal string
  | Nanoseconds int64
  | DateTime string
  | Tag String
```

In a language without sum types, we can use multiple methods:
```
Tokenize : () -> (Kind | error)
Int64: () -> (int64 | error)
Float64: () -> (float64 | error)
Bytes: () -> ([]byte | error)
```
We do not need a Boolean or IsNull method, since `true`, `false` and `null` is represented purely as the `Kind`.
Optionally we can also use the Bytes method for Strings.

Some languages have specific optimizations available, for example in Go:
```go
Token() (Kind, []byte, error)
```
We can cast `[]byte` to `string`, `float64` or `int64` (without copying or allocating memory) based on the `Kind`.

## Implementations

<table>

<tr>
<th></th>
<th>XML</th>
<th>JSON</th>
<th>Protobufs</th>
</tr>

<tr>
<td><a href="https://github.com/katydid/parser-go">Golang</a></td>
<td><a href="https://github.com/katydid/parser-go-xml">✅*</a></td>
<td><a href="https://github.com/katydid/parser-go-json">✅*</a></td>
<td><a href="https://github.com/katydid/parser-go-proto">✅*</a></td>
</tr>

<tr>
<td><a href="https://github.com/katydid/katydid-haskell">Haskell</a></td>
<td><a href="https://github.com/katydid/katydid-haskell/blob/master/src/Data/Katydid/Parser/Xml.hs">✅*</a></td>
<td><a href="https://github.com/katydid/katydid-haskell/blob/master/src/Data/Katydid/Parser/Json.hs">✅*</a></td>
<td><a href="https://github.com/katydid/katydid-haskell/blob/master/src/Data/Katydid/Parser/Protobuf/Protobuf.hs">✅*</a></td>
</tr>

<tr>
<td>Lean</td>
<td>❌</td>
<td>Planned</td>
<td>❌</td>
</tr>

</table>

*: Implementation is outdated and implement a previous parser design. They need updating to this new parser interface.

## More

* [Design Decisions](./design.md)
* [Examples](./examples.md)
