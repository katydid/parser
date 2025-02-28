# Parser

The Katydid Parser is a generic interface created to be implemented for many serialization formats in a variety of programming languages.

## Interface

We describe the interface in a language agnostic way.
So that this can be used by for implementing a parser for any serialization in almost any programming language.

The interface is limited to the following methods for traversing the parse tree:

* `Next` (parses up to the start of the next token and returns a [`Kind`](https://github.com/katydid/parser/blob/main/design.md#kind) or an error or EOF)
* [`Skip`](https://github.com/katydid/parser/blob/main/design.md#skip) (possibly returns an error or EOF)

The interface also includes the following methods for tokenizing the current token into a value:

* `IsNull` (returns a parse error or no error if the current token represents null)
* `Bool` (returns a bool or a parse error)
* `Bytes` (returns a byte array a parse error)
* `String` (returns a UTF8 string a parse error)
* `Int64` (returns an 64 bit signed integer a parse error)
* `Float64` (returns a double precision float a parse error)

Throwing a catchable exception or Using Maybe/Optional types are also permitted instead of returning errors.

## Open Questions

* Can we shrink this interface:
  + Do we need `String` or is utf8 `Bytes` good enough?
  + Do we need `Int64` and `Float64`?
  + Can we get rid of `IsNull`?

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
<td><a href="https://github.com/katydid/parser-go-xml">✅</a></td>
<td><a href="https://github.com/katydid/parser-go-json">✅</a></td>
<td><a href="https://github.com/katydid/parser-go-proto">✅</a></td>
</tr>

<tr>
<td><a href="https://github.com/katydid/katydid-haskell">Haskell</a></td>
<td><a href="https://github.com/katydid/katydid-haskell/blob/master/src/Data/Katydid/Parser/Xml.hs">✅</a></td>
<td><a href="https://github.com/katydid/katydid-haskell/blob/master/src/Data/Katydid/Parser/Json.hs">✅</a></td>
<td><a href="https://github.com/katydid/katydid-haskell/blob/master/src/Data/Katydid/Parser/Protobuf/Protobuf.hs">✅</a></td>
</tr>

<tr>
<td>Lean</td>
<td>❌</td>
<td>Planned</td>
<td>❌</td>
</tr>

</table>

Note: Some of these implementations are outdated and implement a previous design of the interface.

## More

* [Design Decisions](./design.md)
* [Examples](./examples.md)