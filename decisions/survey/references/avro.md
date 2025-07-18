# Avro

## Basic Types

* null
* boolean

## String Types

* string: unicode character sequence

## Byte Array Types

* bytes
* Fixed

## Decimal Types

* decimal: The decimal logical type represents an arbitrary-precision signed decimal number (Arbitrary-precision Two’s Complement signed decimal numbers)

## Float64 Types

* float: single precision (32-bit) IEEE 754 floating-point number (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)
* double: double precision (64-bit) IEEE 754 floating-point number (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)

## Int64 Types

* int: 32-bit signed integer (32-bit and 64-bit ZigZag-encoded Little Endian Base 128 (LEB128) variable-length integers)
* long: 64-bit signed integer (32-bit and 64-bit ZigZag-encoded Little Endian Base 128 (LEB128) variable-length integers)

## Date Types

* Date (days from the UNIX Epoch)

## Timestamp Types

* Time (milliseconds and microseconds)
* Timestamp (milliseconds and microseconds)

## Duration Types

* Duration

## Enum Types

* Enums

## List Types

* array

## Union Types

* Unions, as mentioned above, are represented using JSON arrays.

## Object Types

* record
* map

## Uuid Types

* Uuid

## Referenced

* null: no value
* boolean: a binary value
* string: unicode character sequence (Note that since UTF-8 is used as the binary encoding for strings)
* decimal: The decimal logical type represents an arbitrary-precision signed decimal number (Arbitrary-precision Two’s Complement signed decimal numbers)
* bytes: sequence of 8-bit unsigned bytes
* Fixed (`fixed MD5(16);` This example defines a fixed-length type called MD5 which contains 16 bytes.)
* float: single precision (32-bit) IEEE 754 floating-point number (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)
* double: double precision (64-bit) IEEE 754 floating-point number (Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers)
* int: 32-bit signed integer (32-bit and 64-bit ZigZag-encoded Little Endian Base 128 (LEB128) variable-length integers)
* long: 64-bit signed integer (32-bit and 64-bit ZigZag-encoded Little Endian Base 128 (LEB128) variable-length integers)
* Enums
* array
* Unions, as mentioned above, are represented using JSON arrays.
* record	object	{"a": 1}
* map	object	{"a": 1} (Map keys are assumed to be strings.)

### Date-Time

* Date (days from the UNIX Epoch)
* Time (milliseconds and microseconds)
* Timestamp (milliseconds and microseconds)
* Duration

### References

* https://avro.apache.org/docs/1.11.1/specification/
* https://avro.apache.org/docs/1.12.0/specification/#decimal
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"
* https://avro.apache.org/docs/1.11.1/specification/#enums
* https://avro.apache.org/docs/1.11.1/idl-language/