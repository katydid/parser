# Avro

* null
* boolean

## Specification

* null: no value
* boolean: a binary value
* int: 32-bit signed integer
* long: 64-bit signed integer
* float: single precision (32-bit) IEEE 754 floating-point number
* double: double precision (64-bit) IEEE 754 floating-point number
* bytes: sequence of 8-bit unsigned bytes
* string: unicode character sequence
* record	object	{"a": 1}
* enum	string	"FOO"
* array	array	[1]
* map	object	{"a": 1}
* fixed	string	"\u00ff"
* Unions, as mentioned above, are represented using JSON arrays.

## References

* https://avro.apache.org/docs/1.11.1/specification/