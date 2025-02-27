# Thrift

## Basic Types

* null is not serialized
* bool

## String Types

* string

## Byte Array Types

* binary

## Float64 Types

* double: A 64-bit floating point number (Values of type double are first converted to an int64 according to the IEEE 754 floating-point "double format" bit layout.) (Little Endian 64-bit IEEE 764 floating-point numbers)

## Int64 Types

* byte: An 8-bit signed integer
* i16: A 16-bit signed integer (16-bit, 32-bit, and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers)
* i32: A 32-bit signed integer (16-bit, 32-bit, and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers)
* i64: A 64-bit signed integer (16-bit, 32-bit, and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers)

## Enum Types

* enum

## List Types

* list

## Referenced

* bool: A boolean value (true or false)
* string: A text string encoded using UTF-8 encoding
* binary: a sequence of unencoded bytes
* double: A 64-bit floating point number (Values of type double are first converted to an int64 according to the IEEE 754 floating-point "double format" bit layout.) (Little Endian 64-bit IEEE 764 floating-point numbers)
* byte: An 8-bit signed integer
* i16: A 16-bit signed integer (16-bit, 32-bit, and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers)
* i32: A 32-bit signed integer (16-bit, 32-bit, and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers)
* i64: A 64-bit signed integer (16-bit, 32-bit, and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers)
* enum
* list
* struct
* set
* map
* optional
* required

### References

* https://thrift.apache.org/docs/types
* https://thrift.apache.org/docs/idl
* https://github.com/apache/thrift/blob/master/doc/specs/thrift-binary-protocol.md
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"
* https://diwakergupta.github.io/thrift-missing-guide/#_enums