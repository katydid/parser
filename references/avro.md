# Avro

* null
* boolean
* string
* bytes

## String Types

* string: unicode character sequence
* enum	string	"FOO"
* fixed	string	"\u00ff"

## Byte Array Types

* bytes

## Referenced

* null: no value
* boolean: a binary value
* string: unicode character sequence
* enum	string	"FOO"
* fixed	string	"\u00ff"
* bytes: sequence of 8-bit unsigned bytes
* int: 32-bit signed integer
* long: 64-bit signed integer
* float: single precision (32-bit) IEEE 754 floating-point number
* double: double precision (64-bit) IEEE 754 floating-point number
* record	object	{"a": 1}
* array	array	[1]
* map	object	{"a": 1}
* Unions, as mentioned above, are represented using JSON arrays.

### References

* https://avro.apache.org/docs/1.11.1/specification/