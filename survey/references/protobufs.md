# Google Protocol Buffers

## Basic Types

* null
* Empty (message)
* bool

## String Types

* string

## Byte Array Types

* bytes

## Float64 Types

* float: Floating point values are represented using 64-bit (double precision) IEEE754 format (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers).
* double: Floating point values are represented using 64-bit (double precision) IEEE754 format (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers).	

## Uint64 Types

* uint32:	Uses variable-length encoding. Little Endian Base 128 (LEB128).
* uint64:	Uses variable-length encoding. Little Endian Base 128 (LEB128).
* fixed32:	Always four bytes. More efficient than uint32 if values are often greater than 228.
* fixed64:	Always eight bytes. More efficient than uint64 if values are often greater than 256.

## Int64 Types

* int32:	Uses variable-length encoding. Little Endian Base 128 (LEB128). Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead.
* int64:	Uses variable-length encoding. Little Endian Base 128 (LEB128). Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead.
* sint32:	Uses variable-length encoding. ZigZag-encoded Little Endian Base 128. Signed int value. These more efficiently encode negative numbers than regular int32s.
* sint64:	Uses variable-length encoding. ZigZag-encoded Little Endian Base 128. Signed int value. These more efficiently encode negative numbers than regular int64s.
* sfixed32:	Always four bytes.
* sfixed64:	Always eight bytes.

## Timestamp Types

* Timestamp

## Duration Types

* Duration

## Enum Types

* enum
* Field.Cardinality (enum)
* Field.Kind (enum)
* Syntax (enum)

## List Types

* repeated

## Union Types

* oneof

## Map Types

* maps

## Object Types

* message
* Any (message)
* Api (message)
* Field (message)
* FieldMask (message)
* Method (message)
* Mixin (message)
* SourceContext (message)
* Struct (message)
* Type (message)

## Optional Types

These are not encoded or should be treated as not encoded

* optional
* Option (message)

## Referenced

### Builtin

* bool
* string:	A string must always contain UTF-8 encoded or 7-bit ASCII text, and cannot be longer than 232.
* bytes:	May contain any arbitrary sequence of bytes no longer than 232.
* float: Floating point values are represented using 64-bit (double precision) IEEE754 format (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers).
* double: Floating point values are represented using 64-bit (double precision) IEEE754 format (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers).	
* int32:	Uses variable-length encoding. Little Endian Base 128 (LEB128). Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead.
* int64:	Uses variable-length encoding. Little Endian Base 128 (LEB128). Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead.
* uint32:	Uses variable-length encoding. Little Endian Base 128 (LEB128).
* uint64:	Uses variable-length encoding. Little Endian Base 128 (LEB128).
* sint32:	Uses variable-length encoding. ZigZag-encoded Little Endian Base 128. Signed int value. These more efficiently encode negative numbers than regular int32s.
* sint64:	Uses variable-length encoding. ZigZag-encoded Little Endian Base 128. Signed int value. These more efficiently encode negative numbers than regular int64s.
* fixed32:	Always four bytes. More efficient than uint32 if values are often greater than 228.
* fixed64:	Always eight bytes. More efficient than uint64 if values are often greater than 256.
* sfixed32:	Always four bytes.
* sfixed64:	Always eight bytes.
* enum
* repeated
* oneof
* maps
* message
* optional

### Well Known

Well-Known Types that end in “Value” are wrapper messages for other types, such as BoolValue and EnumValue. These are now obsolete.

* Empty (message)
* Timestamp (message)
* Duration (message)
* Any (message)
* Api (message)
* Field (message)
* Field.Cardinality (enum)
* Field.Kind (enum)
* FieldMask (message)
* Method (message)
* Mixin (message)
* Option (message)
* SourceContext (message)
* Struct (message)
* Syntax (enum)
* Type (message)

### References

* https://protobuf.dev/reference/protobuf/google.protobuf/#null-value
* https://protobuf.dev/reference/protobuf/google.protobuf/
* https://protobuf.dev/programming-guides/editions/
* https://protobuf.com/docs/language-spec
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"
* https://protobuf.dev/programming-guides/enum/
