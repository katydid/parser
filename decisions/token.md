# Token

The `Token` method returns a `Kind`, value or an error.

```
Token: () -> (Token | error)
```

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

In languages without sum types we recommend representing a `Token` and as a `Kind` and a value:

```
Token: () -> ((Kind, value) | error)
```

Where [Kind](./kind.md) is a character.

The `Token` method's design varies dependending on implementation language and some experimentation is still required.
We will give some examples.

In a dynamically typed language the return type of a tuple of `Kind` and value is sufficient.

In strongly typed languages without sum types, we can use multiple methods:
```
Tokenize : () -> (Kind | error)
Int64: () -> (int64 | error)
Float64: () -> (float64 | error)
String: () -> (string | error)
Bytes: () -> (list of byte | error)
```
We call the `Tokenize` method first, to get the `Kind` and then call the appropriate follow up method (`Int64`, `Float64` or `Bytes`) to get the value of the token, if required.
We do not need a `Boolean` or `IsVoid` method, since `True`, `False` and `Void` is represented purely as the `Kind`.

Some languages have specific optimizations available, for example in Go:
```go
Token() (Kind, []byte, error)
```
We can cast `[]byte` to `string`, `float64` or `int64` (without copying or allocating memory) based on the `Kind`.