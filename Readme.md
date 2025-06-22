# Parser

The Katydid Parser is a generic interface created to be implemented for many serialization formats in a variety of programming languages.

Our main use case is so that one schema language (for example, JSONSchema, but not limited to) can be applied to any serialization format.
We will use JSON and XML in most examples, but this interface also supports Protobufs and other binary formats.

## Interface

We describe the interface in a language agnostic way, so that this can be used by for implementing a parser for any serialization in almost any programming language.

* `Next : () -> (Hint | error | EOF)`
* `Skip : () -> (error | EOF)?`
* `Token: () -> ((Kind, value) | error)`

### Next

The `Next` method, returns a `Hint`, an error or an `EOF` signal, when no more tokens are left:

```
Next : () -> (Hint | error | EOF)
```

The `Next` method does as little work as possible to move onto the next token and to provide a hint about the kind of token is next.

### Hint

The `Hint` provides a hint about the location in the structure.

In some implementation languages, `Hint` can be indicated with a single byte or ascii character:

* '{': Open
* '}': Close
* 'k': Key
* 'v': Value

In other languages a sum type/enum is preferred to represent `Hint`.

### Skip

The `Skip` method possibly returns an error or EOF:

```
Skip : () -> (error | EOF)?
```

The `Skip` method allows the user to skip over uninteresting parts of the parse tree.
Based on the `Hint` skip has different intuitive behaviours. 

If the `Hint` was:
* '{': these key-value pairs are skipped, including the close `}`.
* 'k': the key's value is skipped.
* 'v': the rest of the key-value pairs are skipped, including the close `}`.
* '}': same as calling `Next` and ignoring the `Hint`.

### Kind

The `Kind` represents the kind of the value:

* '_': Void (also Null or Unit)
* 'e': Elem (a list element)
* 't': True
* 'f': False
* 'x': Bytes (Bytes)
* '"': String (String)
* '-': Int64 (Int64)
* '.': Float64 (Float64)
* '/': Decimal (String)
* '9': Nanoseconds (Int64) (used for duration and time since epoch)
* 'T': Date Time ISO 8601 (String)
* '#': Custom Tag (String)

Note how each `Kind` is mapped to a value type, that will represent the value returned by the `Token` method.

### Token

The `Token` method returns (a `Kind` and a value) or an error.

```
Token: () -> ((Kind, value) | error)
```

The value is represented as one of the following value types:

* `Bytes`
* `String`
* `Int64`
* `Float64`

See the mapping from `Kind` to value types in the previous section.

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

## Examples

* [JSON](./examples/json.md)
* XML **TODO**

## Design Decisions

* [Notation](./decisions/notation.md)
* [Interface](./decisions/interface.md)
* [More](./decisions/)
