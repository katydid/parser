# Kind

We support a specific set of `Kind`s:

* '_': Null (Unit)
* 't': True
* 'f': False
* 'x': Bytes (Bytes)
* '"': String (String)
* '-': Int64 (Int64)
* '.': Float64 (Float64)
* '/': Decimal (String)
* '9': Nanoseconds (Int64) (used for duration and time)
* 'T': Date Time ISO 8601 (String)
* '#': Custom Tag (String)

## Survey

The decision was made by making a [survey of the most common serialization formats](./survey/Readme.md).
We found that a limited amount of scalar types need to be supported:

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

Types can be mapped from rarer types to these supported types. 
For example, UUID is mapped to `Bytes` and Dates to `String` via ISO 8601.