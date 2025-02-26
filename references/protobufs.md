# Google Protocol Buffers

* null values are not serialized
* Empty (message)
* bool
* string

## String Types

* string

## Referenced

### Builtin

* bool
* string:	A string must always contain UTF-8 encoded or 7-bit ASCII text, and cannot be longer than 232.
* message
* repeated
* optional
* oneof
* maps
* enum
* double	
* float	
* int32:	Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead.
* int64:	Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead.
* uint32:	Uses variable-length encoding.
* uint64:	Uses variable-length encoding.
* sint32:	Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s.
* sint64:	Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s.
* fixed32:	Always four bytes. More efficient than uint32 if values are often greater than 228.
* fixed64:	Always eight bytes. More efficient than uint64 if values are often greater than 256.
* sfixed32:	Always four bytes.
* sfixed64:	Always eight bytes.
* bytes:	May contain any arbitrary sequence of bytes no longer than 232.

### Well Known

* Any (message)
* Api (message)
* Duration (message)
* Enum (message)
* Empty (message)
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
* Timestamp (message)
* Type (message)

### References

* https://protobuf.dev/reference/protobuf/google.protobuf/
* https://protobuf.dev/programming-guides/editions/