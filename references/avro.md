# Avro

## Basic Types

* null
* boolean

## String Types

* string: unicode character sequence
* enum	string	"FOO"
* fixed	string	"\u00ff"

## Byte Array Types

* bytes

## Decimal Types

* decimal

## Float64 Types

* float: single precision (32-bit) IEEE 754 floating-point number
* double: double precision (64-bit) IEEE 754 floating-point number

## Referenced

* null: no value
* boolean: a binary value
* string: unicode character sequence
* decimal: The decimal logical type represents an arbitrary-precision signed decimal number
* enum	string	"FOO"
* fixed	string	"\u00ff"
* bytes: sequence of 8-bit unsigned bytes
* float: single precision (32-bit) IEEE 754 floating-point number
* double: double precision (64-bit) IEEE 754 floating-point number
* int: 32-bit signed integer
* long: 64-bit signed integer
* record	object	{"a": 1}
* array	array	[1]
* map	object	{"a": 1}
* Unions, as mentioned above, are represented using JSON arrays.

### References

* https://avro.apache.org/docs/1.11.1/specification/
* https://avro.apache.org/docs/1.12.0/specification/#decimal