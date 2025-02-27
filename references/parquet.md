# Parquet

## Basic Types

* NULL
* BOOLEAN

## String Types

* UTF8

## Byte Array Types

* BYTE_ARRAY: arbitrarily long byte arrays
* FIXED_LEN_BYTE_ARRAY: fixed length byte arrays

## Decimal Types

* INT96: 96 bit signed ints
* DECIMAL

## Float64 Types

* FLOAT16
* FLOAT: IEEE 32-bit floating point values
* DOUBLE: IEEE 64-bit floating point values

## Int64 Types

* INT32: 32 bit signed ints
* INT64: 64 bit signed ints

## Date Types

* DATE

## Timestamp Types

* TIME
* TIMESTAMP

## Enum Types

* ENUM

## List Types

* LIST
* REPEATED

## Map Types

* MAP
* MAP_KEY_VALUE

## Object Types

* MAP
* MAP_KEY_VALUE

## Extra Types

* OPTIONAL
* UUID
* GEOMETRY
* GEOGRAPHY

## Referenced

* NULL values are not encoded in the data. 
* BOOLEAN: 1 bit boolean
* UTF8
* BYTE_ARRAY: arbitrarily long byte arrays
* FIXED_LEN_BYTE_ARRAY: fixed length byte arrays
* INT96: 96 bit signed ints
* DECIMAL
* FLOAT16
* FLOAT: IEEE 32-bit floating point values
* DOUBLE: IEEE 64-bit floating point values
* INT32: 32 bit signed ints
* INT64: 64 bit signed ints
* DATE
* TIME
* TIMESTAMP
* ENUM
* LIST
* REPEATED
* MAP
* MAP_KEY_VALUE
* REQUIRED
* OPTIONAL
* UUID
* GEOMETRY
* GEOGRAPHY

### References

* https://parquet.apache.org/docs/file-format/types/
* https://github.com/apache/parquet-format/blob/master/README.md
* https://github.com/apache/parquet-format/blob/ae5b9d70a7cb9adf2048947f1b7e5d8fdea8564a/LogicalTypes.md?plain=1#L863