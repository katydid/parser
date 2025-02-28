# Parser

The Katydid Parser is a generic interface created to be implemented for many serialization formats in a variety of programming languages.

We describe the interface in a language agnostic way.
So that this can be used by for implementing a parser for any serialization in almost any programming language.

The interface is limited to the following methods for traversing the parse tree:

* `Next` (returns a Kind or an error or EOF)
* `Skip` (possibly returns an error or EOF)

The interface also includes the following methods for tokenizing the current token into a value:

* `IsNull` (returns a parse error or no error if the current token represents null)
* `Bool` (returns a bool or a parse error)
* `Bytes` (returns a byte array a parse error)
* `String` (returns a UTF8 string a parse error)
* `Int64` (returns an 64 bit signed integer a parse error)
* `Float64` (returns a double precision float a parse error)

Note: Throwing a catchable exception or Using Maybe/Optional types are also permitted instead of returning errors.

Optional optimization methods:

* Init (resets the buffer to parse without allocating a new parser)

## Design

This document describes how design decisions were made.

Our main use case is so that one schema language (for example, JSONSchema) can be applied to many different formats.
This usually results in the parser becoming a bottleneck, in which we recommend:

* The parser only ever moves forward and does not do any backtracking.
* The parser should avoid copying or allocating memory on the heap as much as possible.
* The parser should only parse what truly needs parsing and skip as much as possible.

Given these constraints and the fact that most serialization formats are Sequential, we have decided to have two main methods for moving forward:

* Next
* Skip

The parser interface's main method is a `Next` method, which returns a `Kind` or an error.
The `Kind` is a hint about how to traverse the parse tree or tokenize the token.

We also include several tokenization methods:

* `IsNull`
* `Bool`
* `Bytes`
* `String`
* `Int64`
* `Float64`

Deciding which types to represent took us on a journey of doing a [survey](./survey/Readme.md) of the most common serialization formats,
we have come with a limited set of supported [Scalar](./scalar.md) and [Compound](./compound.md) types:

* `Null`
* `Boolean`
* `Bytes`
* `String` (UTF-8)
* `Int64` (for precise and efficient comparisons for integers up to int64)
* `Float64` (for efficient comparisons for floats up to int64)
* Decimals or Uint64s outside of the range of `Float64` or `Int64` respectively are supported as a `String` in JSON's number format.
* Times and Duration are supported via `Int64` (nanoseconds since January 1, 1970 UTC) or a fallback to `String` (ISO 8601).
* `List`
* `Map`

Other types can be mapped from these rared types to these supported types. 
For example, UUID is mapped to `Bytes`, Dates to `String` via ISO 8601, Set to `List` and an Object is repesented as a `Map`.

The `Kind` is indicated with a single byte or ascii character:

* 'n': Null
* '?': Boolean
* 'x': Bytes
* '"': String
* '0': Unknown Number (try Int64, then Float64 and finally String)
* '-': Int64
* 'f': Float64
* '.': Decimal
* 't': Time (try Int64 and then String)
* '{': Map Opened
* '}': Map Closed
* '[': List Opened
* ']': List Closed

The `Skip` method allows the user to skip over uninteresting parts of the parse tree:

* If the Kind '{' was returned by `Next`, then the whole `Map` is skipped.
* If a `Map`'s key was just parsed, then that key's value is skipped.
* If a `Map`'s value was just parsed, then the rest of the `Map` is skipped.
* If the Kind '[' was returned by `Next`, then the whole `List` is skipped.
* If a `List` element was parsed, then the rest of the `List` is skipped.
* In any other case, `Skip` simply calls `Next` and ignores the `Kind`.

