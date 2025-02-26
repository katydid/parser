# FlatBuffers

* bool
* String
* [byte]
* [ubyte]

## String Types

* String: UTF-8 or 7-bit ASCII

## Byte Array Types

* [byte]
* [ubyte]

## Referenced

* bool
* String: UTF-8 or 7-bit ASCII
* For other text encodings or general binary data use vectors ([byte] or [ubyte]) instead
* byte
* ubyte
* Tables: consist of a name (here Monster) and a list of fields
* Optional
* Required
* Struct: Similar to a table, structs consist of fields are required (so no defaults either), and fields may not be added or be deprecated.
* Arrays are a convenience short-hand for a fixed-length collection of elements. (Only supported in structs)
* short (int16)
* ushort (uint16)
* int (int32)
* uint (uint32)
* long (int64)
* ulong (uint64)
* float (float32)
* double (float64)
* Vector (nested vectors are not supported)
* Enums
* Union

### References

* https://flatbuffers.dev/schema/