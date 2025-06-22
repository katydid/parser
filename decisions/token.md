# Token

The `Token` method returns a `Kind`, value or an error.

```
Token: () -> ((Kind, value) | error)
```

Most `Kind`s of tokens include a value:

* '_': Void (also Null or Unit)
* 'e': Elem (a list element)
* 't': True (None)
* 'f': False (None)
* 'x': Bytes (Bytes)
* '"': String (String)
* '-': Int64 (Int64)
* '.': Float64 (Float64)
* '/': Decimal (String)
* '9': Nanoseconds (Int64) (used for duration and time)
* 'T': Date Time ISO 8601 (String)
* '#': Custom Tag (String)

We try to keep the types of values limited to a minimum and to types found in most languages.

Your language will need the following basic types:

* Bytes
* Int64 (for precise and efficient comparisons for integers up to int64)
* Float64 (for efficient comparisons for floats up to 64 bits)

An optional value type is:

* String (UTF-8 decoded)

This is only necessary if a `String` cannot be effectively represented as `Bytes` in your implementation language.

The following values are encoded as other values to keep the number of methods to a minimum:

* Decimals or Uint64s outside of the range of Float64 or Int64 respectively are supported as a String (**TODO: What is that exact string format**).
* Times and Duration are supported via Int64 (nanoseconds since January 1, 1970 UTC) or a fallback to String (ISO 8601).

## Implementations in various languages

The `Token` method is the only method that returns the value of a token.
The `Token` method's design varies dependending on implementation language and some experimentation is still required.
We will give some examples.

In a dynamically typed language the above description of the `Token` method is sufficient.

In a language with sum types, we recommend declaring `Token` as a sum type and not using `Kind`:
```
GetToken : () -> (Token | error)

data Token =
  | Void
  | Elem
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
We call the `Tokenize` method first, to get the `Kind` and then call the appropriate follow up method (`Int64`, `Float64` or `Bytes`) to get the value of the token, if required.
We do not need a `Boolean` or `IsVoid` method, since `true`, `false` and `void` is represented purely as the `Kind`.

Some languages have specific optimizations available, for example in Go:
```go
Token() (Kind, []byte, error)
```
We can cast `[]byte` to `string`, `float64` or `int64` (without copying or allocating memory) based on the `Kind`.