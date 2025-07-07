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
* GEOMETRY
* GEOGRAPHY

## Uuid Types

* UUID

## Optional Types

These are not encoded or should be treated as not encoded

* OPTIONAL

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

### Additional Notes

Parquet supports `null`, `null` values are not encoded in the data but in the definition levels

> Nullity is encoded in the definition levels (which is run-length encoded). NULL values are not encoded in the data. For example, in a non-nested schema, a column with 1000 NULLs would be encoded with run-length encoding (0, 1000 times) for the definition levels and nothing else. https://github.com/apache/parquet-format#nulls

Parquet supports `Uint64`, it would be annotated as `INT(64, false)`

> INT(8, false), INT(16, false), and INT(32, false) must annotate an `int32` primitive type and INT(64, false) must annotate an `int64` primitive type. https://github.com/apache/parquet-format/blob/master/LogicalTypes.md#unsigned-integers

The equivalent for DURATION in Parquet is `INTERVAL`

> https://github.com/apache/parquet-format/blob/master/LogicalTypes.md#interval

### References

* https://parquet.apache.org/docs/file-format/types/
* https://github.com/apache/parquet-format/blob/master/README.md
* https://github.com/apache/parquet-format/blob/ae5b9d70a7cb9adf2048947f1b7e5d8fdea8564a/LogicalTypes.md?plain=1#L863
* https://github.com/apache/iceberg/blob/main/format/spec.md#crs
