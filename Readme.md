# Parser

The Katydid Parser is a generic interface created to be programming language agnostic and serialization format agnostic.
This is so that it can be implemented for many serialization formats in a variety of programming languages.

Our main use case is so that one schema language (for example, JSONSchema, but not limited to) can be applied to any serialization format.
We will use JSON and XML in most examples, but this interface also supports Protobufs and other binary formats.

## Interface

We describe the [interface](./decisions/interface.md) in a language agnostic [notation](./decisions/notation.md):

* `Next : () -> (Hint | error | EOF)`
* `Skip : () -> (error | EOF)?`
* `Token: () -> (Token | error)`

### Next

The `Next` method, returns a `Hint`, an [error](./decisions/error.md) or an [EOF signal](./decisions/eof.md), when no more tokens are left:

```
Next : () -> (Hint | error | EOF)
```

The `Next` method does as little work as possible to move onto the next token and to provide a `Hint` about what kind of token is next.

### Hint

The [Hint](./decisions/hint.md) provides a hint about the location in the structure.

In some implementation languages, `Hint` can be indicated with a single byte or ascii character, in others using a sum type:

```elm
type Hint =
    Enter -- '{'
  | Leave -- '}'
  | Field -- 'F'
  | Value -- 'V'
```

### Skip

The `Skip` method possibly returns an error or EOF:

```
Skip : () -> (error | EOF)?
```

The `Skip` method allows the user to skip over uninteresting parts of the parse tree.
Based on the `Hint` skip has different intuitive behaviours. 

If the `Hint` was:
* '{': these nodes are skipped, including `}`.
* 'F': the label's children are skipped.
* 'V': the rest of the siblings are skipped, including `}`.
* '}': same as calling `Next` and ignoring the `Hint`.

### Token

The [Token](./decisions/token.md) method returns a `Token` (which consists of a `Kind` and a value) or an error.

```
Token: () -> (Token | error)
```

The value is represented as one of the following value types:

* `Bytes`
* `String`
* [Int64](./decisions/int64.md)
* [Float64](./decisions/float64.md)

The Token type maps each Kind to a value type:

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

Note that `Void`, `Elem`, `False` and `True` have no associated values.

In case your language does not support sum types, you can represent the `Token` method as a tuple of [Kind](./decisions/kind.md) and `value`, where the `Kind` is the character mentiond in the comments above:

```
Token: () -> ((Kind, value) | error)
```

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
