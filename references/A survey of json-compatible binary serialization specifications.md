This data was originally sourced from "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"

# ASN.1

## Composite

* Choice
* Enum
* Set
* Sequence

## Numeric

* Big Endian Two’s Complement signed integers of user-defined length
* Big Endian unsigned integers of user-defined length
* Real numbers consisting of up to 255 bytes encoding the base, scale, exponent, and mantissa
* Arbitrary-length ASCII-encoded decimal numbers

## String

* ASCII
* UTF-8

## Scalars

* Boolean
* Null

## More

* Octet string (byte array)
* Bit-string (arbitrary-length bit array)
* Date
* Time
* Date-time

# JSON

## Composite

* Array
* Object

## Numeric

* Arbitrary-precision ASCII-encoded numbers

## String

* UTF-8

## Scalars

* Boolean
* Null

# XML 

Missing

# Protocol Buffers

## Composite

* Any
* Enum
* List
* Map
* Message
* Oneof
* Struct

## Numeric

* 32-bit and 64-bit Two’s Complement Little Endian Base 128 (LEB128) variable-length signed integers
* 32-bit and 64-bit Little Endian Base 128 (LEB128) variable-length unsigned integers
* 32-bit and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers
* Little Endian 32-bit and 64-bit fixed-length unsigned integers
* Little Endian 32-bit and 64-bit fixed-length Two’s Complement signed integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

## String

* UTF-8

## Scalars

* Boolean

## More

* Bytes (byte array)
* Timestamp
* Duration

# YAML

Missing

# Facebook Thrift

## Composite

* List
* Map
* Set
* Struct
* Union

## Numeric

* 16-bit, 32-bit, and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers
* Little Endian 64-bit IEEE 764 floating-point numbers

## String

* UTF-8

## Scalars

* Boolean

## More

* Binary (byte array)
* Byte

# MessagePack

## Composite

* Array
* Map

## Numeric

* Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Big Endian 7-bit, 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers

## String

* UTF-8

## Scalars

* Boolean
* Nil

## More

* Bin (byte array)
* 32-bit, 64-bit, and 96-bit UNIX seconds and nanoseconds Epoch timestamps

# Apache Avro

## Composite

* Array
* Enum
* Map
* Record
* Union

## Numeric

* 32-bit and 64-bit ZigZag-encoded Little Endian Base 128 (LEB128) variable-length integers
* Arbitrary-precision Two’s Complement signed decimal numbers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

## String

* UTF-8

## Scalars

* Boolean
* Null

## More

* Bytes (variable-length byte array)
* Fixed (fixed-length byte array)
* UUID
* Date (days from the UNIX Epoch)
* Time (milliseconds and microseconds)
* Timestamp (milliseconds and microseconds)
* Duration

# BSON

## Composite

* Array, Document (object)

## Numeric

* Little Endian Two’s Complement signed 32-bit and 64-bit integers
* Little Endian unsigned 64-bit integers
* Little Endian 64-bit and 128-bit IEEE 764 floating-point numbers

## String

* UTF-8

## Scalars

* Boolean
* Null
* Undefined

## More

* Binary data (byte array)
* ObjectId
* Epoch
* DBPointer
* JavaScript code
* Function
* UUID
* MD5
* Symbol
* MongoDB Timestamp
* Regular expression

# Smile

## Composite

* Array
* Object

## Numeric

* 5-bit, 32-bit, and 64-bit ZigZag-encoded signed Little Endian Base 128 (LEB128) variable-length integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers encoded using 7 bit groups
* Arbitrary-length stringified signed integers
* Arbitrary-precision decimals (with scale and stringified integral)

## String

* ASCII
* UTF-8

## Scalars

* Boolean
* Null

## More

* Binary (byte array)

# Microsoft Bond

## Composite

* List
* Maybe
* Nullable
* Set
* Struct
* Vector

## Numeric

* 16-bit, 32-bit, and 64-bit Little Endian Base 128 (LEB128) variable-length unsigned integers
* 16-bit, 32-bit, and 64-bit ZigZag-encoded (4.2) Little Endian Base 128 (LEB128) variable-length signed integers
* Fixed-length 8-bit unsigned integers
* Fixed-length 8-bit Two’s Complement signed integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

## String

* UTF-8
* Little Endian UTF-16

## Scalars

* Boolean

## More

* Blob (byte array)

# UBJSON

## Composite

* Array
* Object

## Numeric

* Big Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Big Endian 8-bit unsigned integers
* Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers
* Arbitrary-precision ASCII-encoded numbers

## String

* UTF-8

## Scalars

* Boolean
* Null

# TOML

Missing

# CapnProto

## Composite

* Enum
* List
* Struct
* Union

## Numeric

* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

## String

* UTF-8

## Scalars

* Bool
* Void

## More

* Data (byte array)

# Apache Parquet

Missing

# CBOR

## Composite

* Array, Map

## Numeric

* Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big unsigned integers
* Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big negative integers (encoded as−1 minus the value)
* Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers
* Big Endian arbitrary-length positive and negative integers
* Arbitrary-precision signed decimals (mantissa and scale-based)

## String

* UTF-8

## Scalars

* Boolean
* Null
* Undefined

## More

* Byte string
* Datetime
* Epoch
* Base64
* Regular expression
* MIME message

# FlatBuffers

## Composite

* Array
* Enum
* Struct
* Table
* Union
* Vector

## Numeric

* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

## String

* UTF-8

## Scalars

* Boolean

# FlexBuffers

## Composite

* Vector
* Map

## Numeric

* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 16-bit, 32-bit, and 64-bit IEEE 764 floating-point numbers

## String

* UTF-8

## Scalars

* Boolean
* Null

## More

* Blob (byte array)


