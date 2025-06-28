# Programming Language Types

A Survey of the 10 most popular plus a few additional ones.

This table shows which languages support the following types and functionality:
* Int64: A 64 bit integer with range MIN: -1 * 2^63 (-9,223,372,036,854,775,808) and MAX: 2^63 - 1 (9,223,372,036,854,775,807)
* Float64: binary64 defined in IEEE-754
* Decimal: Supports parsing of arbitrary precision decimals in ISO 6093 format while preserving the precision.
* Time: Parsing Time RFC 3339 which includes offsets.
* Nano: Parsing Time according to RFC 3339 while perserving and not truncating nanoseconds.
* Zone: Parsing the new Time format, Internet Extended Date/Time Format RFC 9557 that includes named timezones.
* Char: A Char type that can represent visible ascii chars including: '_', 'a'-'z', 'A'-'Z', '"', '-', '.', '/', '0'-'9', '#', '{', '}', '(', ')', '[', ']'
* Bytes: A sequence of 8-bit bytes.
* UTF8Str: Strings are encoded as UTF8 and can convert a sequence of bytes into a UTF-8 string type.
* UTF8Func: Supports UTF-8 string functions for [case folding](https://www.unicode.org/L2/L2000/00261-tr25-0d1.html) and normalization (nfc, nfd, nfkc, and nfkd).
* Sum: Sum Types or Tagged Unions with exhaustive pattern matching.

**TODO: Double check that decimal libraries actually support parsing**

<table>
  <tr>
    <th>Language</th>
    <th>Int64</th>
    <th>Float64</th>
    <th>Decimal</th>
    <th>Time</th>
    <th>Nano</th>
    <th>Zone</th>
    <th>Char</th>
    <th>Bytes</th>
    <th>UTF8Str</th>
    <th>UTF8Func</th>
    <th>Sum</th>
  </tr>
  <tr>
    <td><a href="./references/javascript.md">Javascript</a></td>
    <td>✔️</td>
    <td>✅</td>
    <td>☑</td>
    <td>✅</td>
    <td>☑</td>
    <td>☑</td>
    <td>❌</td>
    <td></td>
    <td></td>
    <td></td>
    <td>❌</td>
  </tr>
  <tr>
    <td><a href="./references/python.md">Python</a></td>
    <td>✔️</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>❌</td>
    <td>✔️</td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
  </tr>
  <tr>
    <td><a href="./references/java.md">Java</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td></td>
    <td>❌</td>
  </tr>
  <tr>
    <td><a href="./references/csharp.md">C#</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td></td>
    <td>☑</td>
  </tr>
  <tr>
    <td><a href="./references/cpp.md">C++</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
  </tr>
  <tr>
    <td><a href="./references/c.md">C</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>❌</td>
    <td>❌</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td></td>
    <td>❌</td>
  </tr>
  <tr>
    <td><a href="./references/php.md">PHP</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>✅</td>
    <td>☑</td>
    <td>❌</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td></td>
    <td>❌</td>
  </tr>
  <tr>
    <td><a href="./references/golang.md">Golang</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
  </tr>
  <tr>
    <td><a href="./references/rust.md">Rust</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>☑</td>
    <td>☑</td>
    <td>☑</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td></td>
    <td>✅</td>
  </tr>
  <tr>
    <td><a href="./references/swift.md">Swift</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>✅</td>
    <td>❌</td>
    <td>❌</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
  </tr>
  <tr>
    <td><a href="./references/haskell.md">Haskell</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
  </tr>
  <tr>
    <td><a href="./references/erlang.md">Erlang</a></td>
    <td></td>
    <td>❌</td>
    <td>❌</td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
    <td>✔️</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
  </tr>
  <tr>
    <td><a href="./references/lean.md">Lean</a></td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
    <td>✅</td>
  </tr>
</table>

The cell contents indicate the following:
* ✅ = supported natively or via standard library
* ☑ = supported via third party library
* ✔️ = supported natively for our use case of parsing and comparison, but does not conform to other properties of the type. For example `bigint` in `Javascript` supports `int64` for comparison purposes, but not for addition, since bigint won't overflow like `int64` will.
* ❌ = no support

We didn't survey all languages, but we made some assumptions:
* We assume Kotlin, Clojure and Scala has access to everything that Java has and possibly more, for example we know Kotlin and Scala have access to sum types.
* We assume Elixir has access to everything Erlang has and more, for example arbitrary precision [decimals](https://github.com/ericmj/decimal).
* We assume Typescript has access to everything that Javascript has and more, for example Typescript has support for sum types.

Please help us add more languages: Clojure, Cobol, Dart, Delphi, Elixir, Elm, Idris, Julia, Kotlin, Lua, Lisp, Matlab, Objective-C, OCaml, Perl, Prolog, R, Ruby, Scala, TypeScript, Visual Basic, Zig

## Time

Internet Extended Date/Time Format RFC 9557 was published April 2024, so we do not expect a lot of languages to already support it.

## References

Top 15 Programming Languages: JS, Python, Typescript, Java, C#, C++, C, PHP, Go, Rust, Kotlin, Lua, Dart, Ruby, Swift, R - https://survey.stackoverflow.co/2024/technology#most-popular-technologies-language

List of Programming Languages: C, C++, C#, Clojure, Cobol, Dart, Delphi, Elixir, Elm, Erlang, F#, Forth, Fortran, Go, Haskell, Idris, Java, JavaScript, Julia, Kotlin, Lean, Lua, Lisp, Matlab, Objective-C, OCaml, Perl, PHP, Prolog, Python, R, Ruby, Rust, Scala, Swift, TypeScript, Visual Basic, Zig - https://survey.stackoverflow.co/2024/technology#most-popular-technologies-language

* [rfc9557](https://datatracker.ietf.org/doc/html/rfc9557#name-internet-extended-date-time)
* [Larry Garfield's enum-comparison](https://github.com/Crell/enum-comparison)