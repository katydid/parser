# Scalar Types

We did a [survey](./survey/Readme.md) and found the following common scalar types that need to be supported with a basic type in your implementation language:

<table>
<tr><th>Surveyed</th><th>Supported as</th></tr>
<tr><td>Null</td><td>Kind</td></tr>
<tr><td>Bool</td><td>Kind</td></tr>
<tr><td>String</td><td>String</td></tr>
<tr><td>Bytes</td><td>Bytes</td></tr>
<tr><td>Int64</td><td>Int64</td></tr>
<tr><td>Float64</td><td>Float64</td></tr>
<tr><td>Decimal</td><td>String (<b>TODO: What is that exact string format</b>)</td></tr>
<tr><td>Uint64</td><td>Int64 (if in range) or fallback to String (if out of int64 range, same as decimal)</td></tr>
<tr><td>Date</td><td>String: yyyy-mm-dd (ISO 8601)</td></tr>
<tr><td>Time</td><td>Int64 (nanoseconds since January 1, 1970 UTC) or fallback to String (ISO 8601)</td></tr>
<tr><td>Duration</td><td>Int64 (nanoseconds)</td></tr>
<tr><td>UUID</td><td>Bytes (16 bytes)</td></tr>
<tr><td>Enum</td><td>String (the string representation of the Enum) or fallback to Int64</td></tr>
</table>

## Basic Types

Your language will need the following basic types:

* Bytes
* String (UTF-8 decoded)
* Int64 (for precise and efficient comparisons for integers up to int64)
* Float64 (for efficient comparisons for floats up to 64 bits)
* Decimals or Uint64s outside of the range of Float64 or Int64 respectively are supported as a String (**TODO: What is that exact string format**).
* Times and Duration are supported via Int64 (nanoseconds since January 1, 1970 UTC) or a fallback to String (ISO 8601).

