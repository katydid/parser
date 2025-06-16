# Types supported by each serialization format

We conducted a survey of a few common serialization formats:

* ASN.1
* JSON
* XML
* Protobufs
* YAML
* Thrift
* MsgPack
* Avro
* BSON
* Smile
* UBJSON
* TOML
* CapnProto
* Parquet
* CBOR
* FlatBuffers
* FlexBuffers

We found that these formats have a lot in common.
Not all formats support all scalar types, but we found there is a lot of overlap between the following scalar types:

* Null
* Boolean
* String (UTF-8)
* Bytes
* Decimal (Arbitrary-precision Decimal Values. This includes integers and floats outside the 64-bit range, which are tough to represent with built-in types in most programming languages.)
* Float64 (Double-precision floating-point format IEEE-754)
* Int64 (Includes Int32, Int16, Int8)
* Uint64 (Includes Uint32, Uint16, Uint8, but most importantly must include values outside the range of int64)
* Date
* Time
* Duration
* UUID
* Enum

Note: ASN.1 also has an Arbitrary-length bit array.

Composing these scalar types can be composed using compound types:

* Void (Can be emulated by an empty Object in JSON and many other formats or a message without fields.)
* List (Also referred to as Sequence, Array, Vector, repeated or elements.)
* Set
* Union (Also referred to as Oneof or Choice.)
* Object (These are key-value pairs, where the keys are limited to strings. Also referred to as Struct, Message, Record, Object or Table.)
* Map (Maps are key-value pairs, where the keys are not limited to strings.)

Note: YAML also has `pairs`, which can be treated as lists of length 2.

In our survey we found that All formats support: Bool, String, Float64, Int64, List and Object.
Other types are not supported by all formats and for that it is worth studying this table:

<table>
<tr>
<th></th>
<th>Null</th>
<th>Void</th>
<th>Bool</th>
<th>String</th>
<th>Bytes</th>
<th>Decimal</th>
<th>Float64</th>
<th>Uint64</th>
<th>Int64</th>
<th>Date</th>
<th>Time</th>
<th>Duration</th>
<th>Enum</th>
<th>List</th>
<th>Set</th>
<th>Union</th>
<th>Map</th>
<th>Object</th>
<th>UUID</th>
</tr>

<tr>
<td>ASN.1</td>
<td>✅</td>
<td>❌</td>
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
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>JSON</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
</tr>

<tr>
<td>XML</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>Protobufs</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>YAML</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>Thrift</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>MsgPack</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>Avro</td>
<td>✅</td>
<td>❌</td>
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
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
</tr>

<tr>
<td>BSON</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
</tr>

<tr>
<td>Smile</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>UBJSON</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>TOML</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>CapnProto</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>Parquet</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
</tr>

<tr>
<td>CBOR</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>FlatBuffers</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
</tr>

<tr>
<td>FlexBuffers</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>❌</td>
<td>❌</td>
<td>✅</td>
<td>✅</td>
<td>❌</td>
</tr>

</table>

## References

* See the [references folder](./references/)
