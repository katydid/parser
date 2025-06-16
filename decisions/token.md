# Token

Most `Kind`s of tokens include a value:

* '_': Null (None)
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