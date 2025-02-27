# CBOR

## Basic Types

* null
* boolean

## String Types

* text string

## Byte Array Types

* byte string	N bytes

## Decimal Types

* Decimal Fractions and Bigfloats

## Float64 Types

* float: representable by IEEE 754 binary64

## Referenced

* null
* boolean
* text string	N bytes (UTF-8 text)
* byte string	N bytes
* Decimal Fractions and Bigfloats
* float: representable by IEEE 754 binary64
* unsigned integer: 0..264-1
* negative integer: range -264..264-1 inclusive
* array	N data items (elements)
* map	2N data items (key/value pairs)
* tag of number: an integer in the range 0..264-1
* simple
* undefined: a substitute for a data item with an encoding problem.

### References

* https://www.rfc-editor.org/rfc/rfc8949.html#name-extended-generic-data-model
* https://www.rfc-editor.org/rfc/rfc7049#section-2.4.3