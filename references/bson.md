# BSON

## Basic Types

* Null
* Boolean

## String Types

* String
* Regular Expression
* JavaScript

## Byte Array Types

* Binary data
* Function (subtype of binData)
* MD5 (subtype of binData)

## Decimal Types

* Decimal128

## Float64 Types

* Double (8 bytes (64-bit IEEE 754-2008 binary floating point)) (Little Endian 64-bit and 128-bit IEEE 754 floating-point numbers)

## Int64 Types

* 32-bit integer (Little Endian Two’s Complement signed 32-bit and 64-bit integers)
* 64-bit integer (Little Endian Two’s Complement signed 32-bit and 64-bit integers)

## Date Types

* Date

## Timestamp Types

* Timestamp

## List Types

* Array

## Object Types

* Object

## Extra Types

* ObjectId (example: `_id: ObjectId("5099803df3f4948bd2f98391")`)
* Min key
* Max key
* Uuid

## Referenced

* Null
* Boolean
* String
* JavaScript
* Regular Expression
* Binary data
* Function (subtype of binData)
* MD5 (subtype of binData)
* Decimal128
* Double (8 bytes (64-bit IEEE 754-2008 binary floating point)) (Little Endian 64-bit and 128-bit IEEE 754 floating-point numbers)
* 32-bit integer (Little Endian Two’s Complement signed 32-bit and 64-bit integers)
* 64-bit integer (Little Endian Two’s Complement signed 32-bit and 64-bit integers)
* Date
* Timestamp
* Array
* Object
* ObjectId (example: `_id: ObjectId("5099803df3f4948bd2f98391")`)
* Min key
* Max key
* Undefined (Deprecated).
* DBPointer (Deprecated).
* Symbol (Deprecated).

### References

* https://www.mongodb.com/docs/manual/reference/bson-types/
* https://www.mongodb.com/docs/manual/core/document/
* https://bsonspec.org/spec
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"