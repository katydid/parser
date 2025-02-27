# FlexBuffers

## Basic Types

* Null
* Boolean

## String Types

* UTF-8

## Byte Array Types

* Blob (byte array)

## Referenced

* Null
* Boolean
* UTF-8
* Blob (byte array)
* Vector
* Map with keys, but [unlike FlatBuffers it has no restriction on the keys (fields) that you use](https://flatbuffers.dev/flexbuffers/).
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 16-bit, 32-bit, and 64-bit IEEE 764 floating-point numbers

### References

* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"
* https://flatbuffers.dev/flexbuffers/ 