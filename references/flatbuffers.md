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

## Uint64 Types

* ushort (uint16) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)
* uint (uint32) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)
* ulong (uint64) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)

## Int64 Types

* short (int16) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)
* int (int32) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)
* long (int64) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)

## Enum Types

* Enums

## List Types

* Arrays are a convenience short-hand for a fixed-length collection of elements. (Only supported in structs)
* Vector (nested vectors are not supported)

## Union Types

* Union

## Referenced

* bool
* String: UTF-8 or 7-bit ASCII
* For other text encodings or general binary data use vectors ([byte] or [ubyte]) instead
* byte
* ubyte
* float (float32) (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)
* double (float64) (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)
* ushort (uint16) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)
* uint (uint32) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)
* ulong (uint64) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)
* short (int16) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)
* int (int32) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)
* long (int64) (Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)
* Enums
* Arrays are a convenience short-hand for a fixed-length collection of elements. (Only supported in structs)
* Vector (nested vectors are not supported)
* Union
* Tables: consist of a name (here Monster) and a list of fields
* Optional
* Required
* Struct: Similar to a table, structs consist of fields are required (so no defaults either), and fields may not be added or be deprecated.

### References

* https://flatbuffers.dev/schema/
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"