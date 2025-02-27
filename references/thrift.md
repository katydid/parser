# Thrift

## Basic Types

* null is not serialized
* bool

## String Types

* string

## Byte Array Types

* binary

## Float64 Types

* double: A 64-bit floating point number (Values of type double are first converted to an int64 according to the IEEE 754 floating-point "double format" bit layout.)

## Referenced

* bool: A boolean value (true or false)
* string: A text string encoded using UTF-8 encoding
* binary: a sequence of unencoded bytes
* double: A 64-bit floating point number (Values of type double are first converted to an int64 according to the IEEE 754 floating-point "double format" bit layout.)
* byte: An 8-bit signed integer
* i16: A 16-bit signed integer
* i32: A 32-bit signed integer
* i64: A 64-bit signed integer
* struct
* list
* set
* map
* optional
* required

### References

* https://thrift.apache.org/docs/types
* https://thrift.apache.org/docs/idl
* https://github.com/apache/thrift/blob/master/doc/specs/thrift-binary-protocol.md