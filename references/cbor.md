# CBOR

* null
* boolean

## Data-Model

* null
* boolean
* unsigned integer N
* negative integer -1-N
* byte string	N bytes
* text string	N bytes (UTF-8 text)
* array	N data items (elements)
* map	2N data items (key/value pairs)
* tag of number N	1 data item
* simple/float
* undefined: a substitute for a data item with an encoding problem.

## References

* https://www.rfc-editor.org/rfc/rfc8949.html#name-extended-generic-data-model