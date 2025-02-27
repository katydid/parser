# FlatBuffers

## Basic Types

* bool

## String Types

* String: UTF-8 or 7-bit ASCII

## Byte Array Types

* [byte]
* [ubyte]

## Float64 Types

* float (float32) (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)
* double (float64) (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)

## Referenced

* bool
* String: UTF-8 or 7-bit ASCII
* For other text encodings or general binary data use vectors ([byte] or [ubyte]) instead
* byte
* ubyte
* float (float32) (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)
* double (float64) (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)
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
* Vector (nested vectors are not supported)
* Enums
* Union

### References

* https://flatbuffers.dev/schema/
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"