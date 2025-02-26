# CBOR

* null
* boolean
* text string
* byte string

## String Types

* text string

## Byte Array Types

* byte string	N bytes

## Referenced

* null
* boolean
* text string	N bytes (UTF-8 text)
* byte string	N bytes
* unsigned integer N
* negative integer -1-N
* array	N data items (elements)
* map	2N data items (key/value pairs)
* tag of number N	1 data item
* simple/float
* undefined: a substitute for a data item with an encoding problem.

### References

* https://www.rfc-editor.org/rfc/rfc8949.html#name-extended-generic-data-model