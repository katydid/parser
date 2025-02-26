# Apache Parquet

* NULL
* BOOLEAN

## Types

* NULL values are not encoded in the data. 
* BOOLEAN: 1 bit boolean
* INT32: 32 bit signed ints
* INT64: 64 bit signed ints
* INT96: 96 bit signed ints
* FLOAT: IEEE 32-bit floating point values
* DOUBLE: IEEE 64-bit floating point values
* BYTE_ARRAY: arbitrarily long byte arrays
* FIXED_LEN_BYTE_ARRAY: fixed length byte arrays
* UTF8
* MAP
* MAP_KEY_VALUE
* LIST
* REQUIRED
* OPTIONAL
* REPEATED

## References

* https://parquet.apache.org/docs/file-format/types/
* https://github.com/apache/parquet-format/blob/master/README.md