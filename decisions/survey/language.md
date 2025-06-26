# Programming Language Types

A Survey of the 10 most popular plus a few additional ones.

This table shows which languages support the following types and functionality:
* Int64: A 64 bit integer with range MIN: -1 * 2^63 (-9,223,372,036,854,775,808) and MAX: 2^63 - 1 (9,223,372,036,854,775,807)
* Float64: binary64 defined in IEEE-754
* Decimal: Supports parsing of abitrary precision decimals in ISO 6093 format and preserving the precision.
* Time: Parsing Time RFC 3339
* Nano: Parsing Time according to RFC 3339 while perserving and not truncating nanoseconds
* NewTime: Parsing the new Time format, Internet Extended Date/Time Format RFC 9557
* Char: A Char type that can represent visible ascii chars including: '_', 'a'-'z', 'A'-'Z', '"', '-', '.', '/', '0'-'9', '#', '{', '}', '(', ')', '[', ']'
* Bytes: A sequence of 8-bit bytes.
* UTF8: Supports UTF-8 string functions like eqFold, contains, hasSuffix, hasPrefix, toLower, toUpper.
* NativeUTF8: Strings are encoded as UTF8 and can convert a sequence of bytes into a UTF-8 string type.
* Sum: Sum Types or Tagged Unions

<table>
  <tr>
    <th>Language</th>
    <th>Int64</th>
    <th>Float64</th>
    <th>Decimal</th>
    <th>Time</th>
    <th>Nano</th>
    <th>NewTime</th>
    <th>Bytes</th>
    <th>UTF8</th>
    <th>NativeUTF8</th>
    <th>Sum</th>
  </tr>
  <tr>
    <td>Javascript</td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
    <td>☑</td>
    <td>☑</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Python</td>
    <td>✅</td>
    <td></td>
    <td>✅</td>
    <td>✅</td>
    <td>☑</td>
    <td>❌</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Java</td>
    <td>✅</td>
    <td>✅</td>
    <td></td>
    <td>✅</td>
    <td>✅</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>C#</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>C++</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>C</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>PHP</td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
    <td>☑</td>
    <td>❌</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Golang</td>
    <td>✅</td>
    <td>✅</td>
    <td></td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
    <td></td>
    <td></td>
    <td></td>
    <td>❌</td>
  </tr>
  <tr>
    <td>Rust</td>
    <td>✅</td>
    <td>✅</td>
    <td></td>
    <td>☑</td>
    <td>☑</td>
    <td>☑</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Swift</td>
    <td>✅</td>
    <td></td>
    <td></td>
    <td>✅</td>
    <td>❌</td>
    <td>❌</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Haskell</td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
    <td>✅</td>
    <td>❌</td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
  </tr>
  <tr>
    <td>Erlang</td>
    <td></td>
    <td>❌</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
  </tr>
  <tr>
    <td>Lean</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td>✅</td>
  </tr>
</table>

The cell contents indicate the following:
* ✅ = supported natively or via standard library
* ☑ = supported via third party library
* ❌ = no support

We didn't survey all languages, but we made some assumptions:
* We assume Kotlin, Clojure and Scala has access to everything that Java has and possibly more, like sum types.
* We assume Elixir has access to everything Erlang has.
* We assume Typescript has access to everything that Javascript has.

Please help us add more languages: Clojure, Cobol, Dart, Delphi, Elixir, Elm, Idris, Julia, Kotlin, Lua, Lisp, Matlab, Objective-C, OCaml, Perl, Prolog, R, Ruby, Scala, TypeScript, Visual Basic, Zig

## Time

Internet Extended Date/Time Format RFC 9557 was published April 2024, so we do not expect a lot of languages to already support it.

## References

Top 15 Programming Languages: JS, Python, Typescript, Java, C#, C++, C, PHP, Go, Rust, Kotlin, Lua, Dart, Ruby, Swift, R - https://survey.stackoverflow.co/2024/technology#most-popular-technologies-language

List of Programming Languages: C, C++, C#, Clojure, Cobol, Dart, Delphi, Elixir, Elm, Erlang, F#, Forth, Fortran, Go, Haskell, Idris, Java, JavaScript, Julia, Kotlin, Lean, Lua, Lisp, Matlab, Objective-C, OCaml, Perl, PHP, Prolog, Python, R, Ruby, Rust, Scala, Swift, TypeScript, Visual Basic, Zig - https://survey.stackoverflow.co/2024/technology#most-popular-technologies-language

* [rfc9557](https://datatracker.ietf.org/doc/html/rfc9557#name-internet-extended-date-time)