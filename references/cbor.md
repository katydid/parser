# CBOR

## Basic Types

* null
* boolean

## String Types

* text string
* regular expression

## Byte Array Types

* byte string	N bytes

## Decimal Types

* Decimal Fractions and Bigfloats (Arbitrary-precision signed decimals (mantissa and scale-based)) (Big Endian arbitrary-length positive and negative integers)

## Float64 Types

* float: representable by IEEE 754 binary64 (Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers)

## Uint64 Types

* unsigned integer: 0..264-1 (Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big unsigned integers)

## Int64 Types

* negative integer: range -264..264-1 inclusive (Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big negative integers (encoded as−1 minus the value))

## Date Types

* Calendar Dates

## Timestamp Types

* Standard Date/Time String
* Epoch-Based Date/Time

## List Types

* array	N data items (elements)

## Map Types

* map	2N data items (key/value pairs)

## Object Types

* map	2N data items (key/value pairs)

## Extra Types

* tag of number: an integer in the range 0..264-1
* simple
* undefined: a substitute for a data item with an encoding problem.
* Base64 (encoded as text string)
* MIME Message (encoded as text string)

## Referenced

* null
* boolean
* text string	N bytes (UTF-8 text)
* regular expression
* byte string	N bytes
* Decimal Fractions and Bigfloats (Arbitrary-precision signed decimals (mantissa and scale-based)) (Big Endian arbitrary-length positive and negative integers)
* float: representable by IEEE 754 binary64 (Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers)
* unsigned integer: 0..264-1 (Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big unsigned integers)
* negative integer: range -264..264-1 inclusive (Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big negative integers (encoded as−1 minus the value))
* Calendar Dates
* Standard Date/Time String
* Epoch-Based Date/Time
* array	N data items (elements)
* map	2N data items (key/value pairs)
* tag of number: an integer in the range 0..264-1
* simple
* undefined: a substitute for a data item with an encoding problem.
* Base64 (encoded as text string)
* MIME Message (encoded as text string)

### References

* https://www.rfc-editor.org/rfc/rfc8949.html#name-extended-generic-data-model
* https://www.rfc-editor.org/rfc/rfc8949.html#name-standard-date-time-string
* https://www.rfc-editor.org/rfc/rfc8943
* https://www.rfc-editor.org/rfc/rfc7049#section-2.4.3
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"