# Types supported by each serialization format

## TODO

* XML
* YAML
* TOML
* Parquet

## Null

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :white_check_mark: XML ([xsi:nil](https://www.w3.org/TR/xmlschema-1/#xsi_nil))
* :x: Protobufs
* :white_check_mark: YAML
* :x: Thrift
* :white_check_mark: MsgPack
* :white_check_mark: Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :white_check_mark: UBJSON
* :x: TOML
* :x: CapnProto
* :x: Parquet
* :white_check_mark: CBOR
* :x: FlatBuffers
* :white_check_mark: FlexBuffers

## Void

* :x: ASN.1
* :x: JSON
* :x: XML
* :white_check_mark: Protobufs ([empty.proto](https://github.com/protocolbuffers/protobuf/blob/main/src/google/protobuf/empty.proto))
* :x: YAML
* :x: Thrift
* :x: MsgPack
* :x: Avro
* :x: BSON
* :x: Smile
* :white_check_mark: UBJSON (No-Op)
* :x: TOML
* :white_check_mark: CapnProto
* :x: Parquet
* :x: CBOR
* :x: FlatBuffers
* :x: FlexBuffers

It can be emulated by an empty Object in JSON and many other formats or a message without fields.

## Boolean

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :white_check_mark: XML
* :white_check_mark: Protobufs
* :white_check_mark: YAML
* :white_check_mark: Thrift
* :white_check_mark: MsgPack
* :white_check_mark: Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :white_check_mark: UBJSON
* :white_check_mark: TOML
* :white_check_mark: CapnProto
* :white_check_mark: Parquet
* :white_check_mark: CBOR
* :white_check_mark: FlatBuffers
* :white_check_mark: FlexBuffers

## UTF-8 String

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :grey_question: XML
* :white_check_mark: Protobufs
* :grey_question: YAML
* :white_check_mark: Thrift
* :white_check_mark: MsgPack
* :white_check_mark: Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :white_check_mark: UBJSON
* :grey_question: TOML
* :white_check_mark: CapnProto
* :grey_question: Parquet
* :white_check_mark: CBOR
* :white_check_mark: FlatBuffers
* :white_check_mark: FlexBuffers

## Byte Array

* :white_check_mark: ASN.1 (Octet string)
* :x: JSON (possible with base64 encoding)
* :grey_question: XML
* :white_check_mark: Protobufs (bytes)
* :grey_question: YAML
* :white_check_mark: Thrift (binary)
* :white_check_mark: MsgPack (bin)
* :white_check_mark: Avro (bytes and fixed for a fixed-length byte array)
* :white_check_mark: BSON (binary data)
* :white_check_mark: Smile (binary)
* :x: UBJSON
* :grey_question: TOML
* :white_check_mark: CapnProto (data)
* :grey_question: Parquet
* :white_check_mark: CBOR (byte string)
* :x: FlatBuffers
* :white_check_mark: FlexBuffers (blob)

## Arbitrary-precision Decimal Values (decimal)

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :grey_question: XML
* :x: Protobufs
* :grey_question: YAML
* :x: Thrift
* :x: MsgPack
* :white_check_mark: Avro ([Arbitrary-precision Two’s Complement signed decimal numbers](https://avro.apache.org/docs/1.12.0/specification/#decimal))
* :x: BSON (float128)
* :white_check_mark: Smile
* :white_check_mark: UBJSON
* :grey_question: TOML
* :x: CapnProto
* :grey_question: Parquet
* :white_check_mark: CBOR ([Arbitrary-precision signed decimals (mantissa and scale-based)](https://www.rfc-editor.org/rfc/rfc7049#section-2.4.3))
* :x: FlatBuffers
* :x: FlexBuffers

## Numeric

All numeric types are covered by `float64`, `int64`, `uint64` or worst case arbitrary-precision `decimal` values.
Everything could also be covered by one type (for example `int64`) for fast comparisons and covering the rest with an arbitrary-precision decimal values via a `string`.

### ASN.1

decimal:

* Big Endian Two’s Complement signed integers of user-defined length
* Big Endian unsigned integers of user-defined length
* Real numbers consisting of up to 255 bytes encoding the base, scale, exponent, and mantissa
* Arbitrary-length ASCII-encoded decimal numbers

### JSON

decimal:

* Arbitrary-precision ASCII-encoded numbers

### XML

* TODO

### Protobufs

float64, int64 and uint64:

* 32-bit and 64-bit Two’s Complement Little Endian Base 128 (LEB128) variable-length signed integers
* 32-bit and 64-bit Little Endian Base 128 (LEB128) variable-length unsigned integers
* 32-bit and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers
* Little Endian 32-bit and 64-bit fixed-length unsigned integers
* Little Endian 32-bit and 64-bit fixed-length Two’s Complement signed integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### YAML

* TODO

### Thrift

int64 and float64:

* 16-bit, 32-bit, and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers
* Little Endian 64-bit IEEE 764 floating-point numbers

### MsgPack

int64, uint64 and float64:

* Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Big Endian 7-bit, 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### Avro

int64, float64 and decimal:

* 32-bit and 64-bit ZigZag-encoded Little Endian Base 128 (LEB128) variable-length integers
* Arbitrary-precision Two’s Complement signed decimal numbers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### BSON

int64, uint64, float64 and decimal:

* Little Endian Two’s Complement signed 32-bit and 64-bit integers
* Little Endian unsigned 64-bit integers
* Little Endian 64-bit and 128-bit IEEE 764 floating-point numbers

### Smile

int64, float64, decimal:

* 5-bit, 32-bit, and 64-bit ZigZag-encoded signed Little Endian Base 128 (LEB128) variable-length integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers encoded using 7 bit groups
* Arbitrary-length stringified signed integers
* Arbitrary-precision decimals (with scale and stringified integral)

### UBJSON

int64, float64, decimal:

* Big Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Big Endian 8-bit unsigned integers
* Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers
* Arbitrary-precision ASCII-encoded numbers

### TOML

TODO

### CapnProto

int64, uint64, float64:

* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### Parquet

TODO

### CBOR

uint64, int64, float64, decimal:

* Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big unsigned integers
* Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big negative integers (encoded as−1 minus the value)
* Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers
* Big Endian arbitrary-length positive and negative integers
* Arbitrary-precision signed decimals (mantissa and scale-based)

### FlatBuffers

int64, uint64, float64:

* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### FlexBuffers

int64, uint64, float64:

* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 16-bit, 32-bit, and 64-bit IEEE 764 floating-point numbers

## Date/Time/Duration

* :white_check_mark: ASN.1 (Date, Time and Date-time)
* :x: JSON
* :grey_question: XML
* :white_check_mark: Protobufs (Timestamp, Duration)
* :grey_question: YAML
* :x: Thrift
* :white_check_mark: MsgPack (32-bit, 64-bit, and 96-bit UNIX seconds and nanoseconds Epoch timestamps)
* :white_check_mark: Avro
  + Date (days from the UNIX Epoch)
  + Time (milliseconds and microseconds)
  + Timestamp (milliseconds and microseconds)
  + Duration
* :white_check_mark: BSON (MongoDB Timestamp)
* :x: Smile
* :x: UBJSON
* :grey_question: TOML
* :x: CapnProto
* :grey_question: Parquet
* :white_check_mark: CBOR (Datetime, Epoch)
* :x: FlatBuffers
* :x: FlexBuffers

## Struct / Message / Record / Object

* :x: ASN.1
* :white_check_mark: JSON
* :grey_question: XML
* :white_check_mark: Protobufs
* :grey_question: YAML
* :white_check_mark: Thrift
* :x: MsgPack
* :white_check_mark: Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :white_check_mark: UBJSON
* :grey_question: TOML
* :white_check_mark: CapnProto
* :grey_question: Parquet
* :x: CBOR
* :white_check_mark: FlatBuffers
* :x: FlexBuffers

## List / Sequence / Array / Vector

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :grey_question: XML
* :white_check_mark: Protobufs
* :grey_question: YAML
* :white_check_mark: Thrift
* :white_check_mark: MsgPack
* :white_check_mark: Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :white_check_mark: UBJSON
* :grey_question: TOML
* :white_check_mark: CapnProto
* :grey_question: Parquet
* :white_check_mark: CBOR
* :white_check_mark: FlatBuffers
* :white_check_mark: FlexBuffers

## Enum

* :white_check_mark: ASN.1
* :x: JSON
* :grey_question: XML
* :white_check_mark: Protobufs
* :grey_question: YAML
* :white_check_mark: Thrift
* :x: MsgPack
* :white_check_mark: Avro
* :x: BSON
* :x: Smile
* :x: UBJSON
* :grey_question: TOML
* :white_check_mark: CapnProto
* :grey_question: Parquet
* :x: CBOR
* :white_check_mark: FlatBuffers
* :x: FlexBuffers

## Map

* :x: ASN.1
* :x: JSON
* :grey_question: XML
* :white_check_mark: Protobufs
* :grey_question: YAML
* :white_check_mark: Thrift
* :white_check_mark: MsgPack
* :white_check_mark: Avro
* :x: BSON
* :x: Smile
* :x: UBJSON
* :grey_question: TOML
* :x: CapnProto
* :grey_question: Parquet
* :white_check_mark: CBOR
* :x: FlatBuffers
* :white_check_mark: FlexBuffers

## Set

* :white_check_mark: ASN.1
* :x: JSON
* :grey_question: XML
* :x: Protobufs
* :grey_question: YAML
* :white_check_mark: Thrift
* :x: MsgPack
* :x: Avro
* :white_check_mark: BSON
* :x: Smile
* :x: UBJSON
* :grey_question: TOML
* :x: CapnProto
* :grey_question: Parquet
* :x: CBOR
* :x: FlatBuffers
* :x: FlexBuffers

## Union / Oneof / Choice

* :white_check_mark: ASN.1
* :x: JSON
* :grey_question: XML
* :white_check_mark: Protobufs
* :grey_question: YAML
* :white_check_mark: Thrift
* :x: MsgPack
* :white_check_mark: Avro
* :x: BSON
* :x: Smile
* :x: UBJSON
* :grey_question: TOML
* :white_check_mark: CapnProto
* :grey_question: Parquet
* :x: CBOR
* :white_check_mark: FlatBuffers
* :x: FlexBuffers

## Table

FlatBuffers

## UUID

Avro, MongoDB also supports UUID

## Extra ASN.1 types

Arbitrary-length bit array

## Regular expression

MongoDB and CBOR

## Extra MongoDB types

* ObjectId: The 12-byte ObjectId consists of: A 4-byte timestamp, representing the ObjectId's creation, measured in seconds since the Unix epoch. A 5-byte random value generated once per process. This random value is unique to the machine and process. A 3-byte incrementing counter, initialized to a random value.
* DBPointer (Deprecated)
* Javascript
* Function (subtype of binData)
* MD5 (subtype of binData)
* Symbol (Deprecated)
* Undefined (Deprecated)

## Extra CBOR Types

* Base64 (encoded as text string)
* MIME Message (encoded as text string)
* Undefined: a substitute for a data item with an encoding problem.