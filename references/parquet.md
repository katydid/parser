# Parquet

* NULL
* BOOLEAN
* UTF8
* BYTE_ARRAY

## String Types

* UTF8

## Byte Array Types

* BYTE_ARRAY: arbitrarily long byte arrays
* FIXED_LEN_BYTE_ARRAY: fixed length byte arrays

## Referenced

* NULL values are not encoded in the data. 
* BOOLEAN: 1 bit boolean
* UTF8
* BYTE_ARRAY: arbitrarily long byte arrays
* FIXED_LEN_BYTE_ARRAY: fixed length byte arrays
* INT32: 32 bit signed ints
* INT64: 64 bit signed ints
* INT96: 96 bit signed ints
* FLOAT: IEEE 32-bit floating point values
* DOUBLE: IEEE 64-bit floating point values
* MAP
* MAP_KEY_VALUE
* LIST
* REQUIRED
* OPTIONAL
* REPEATED

### References

* https://parquet.apache.org/docs/file-format/types/
* https://github.com/apache/parquet-format/blob/master/README.md