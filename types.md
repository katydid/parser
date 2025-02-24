# Types supported by each serialization format

## TODO

* XML
* YAML
* TOML
* Apache Parquet

## Null

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :white_check_mark: XML (xsi:nil)
* :x: Protocol Buffers (null values are not serialized)
* :grey_question: YAML
* :x: Facebook Thrift
* :white_check_mark: MessagePack
* :white_check_mark: Apache Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :x: Microsoft Bond
* :white_check_mark: UBJSON
* :grey_question: TOML
* :x: CapnProto
* :grey_question: Apache Parquet
* :white_check_mark: CBOR
* :x: FlatBuffers
* :white_check_mark: FlexBuffers

## Void

`void` is only supported by CapnProto, but can also be emulated by an empty Object in JSON and many other formats or a message without fields in for example Protocol Buffers via the [empty](https://github.com/protocolbuffers/protobuf/blob/main/src/google/protobuf/empty.proto) message.

## Boolean

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :grey_question: XML
* :white_check_mark: Protocol Buffers
* :grey_question: YAML
* :white_check_mark: Facebook Thrift
* :white_check_mark: MessagePack
* :white_check_mark: Apache Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :white_check_mark: Microsoft Bond
* :white_check_mark: UBJSON
* :grey_question: TOML
* :white_check_mark: CapnProto
* :grey_question: Apache Parquet
* :white_check_mark: CBOR
* :white_check_mark: FlatBuffers
* :white_check_mark: FlexBuffers

## UTF-8 String

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :grey_question: XML
* :white_check_mark: Protocol Buffers
* :grey_question: YAML
* :white_check_mark: Facebook Thrift
* :white_check_mark: MessagePack
* :white_check_mark: Apache Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :white_check_mark: Microsoft Bond (also Little Endian UTF-16)
* :white_check_mark: UBJSON
* :grey_question: TOML
* :white_check_mark: CapnProto
* :grey_question: Apache Parquet
* :white_check_mark: CBOR
* :white_check_mark: FlatBuffers
* :white_check_mark: FlexBuffers

## Byte Array

* :white_check_mark: ASN.1 (Octet string)
* :x: JSON (possible with base64 encoding)
* :grey_question: XML
* :white_check_mark: Protocol Buffers (bytes)
* :grey_question: YAML
* :white_check_mark: Facebook Thrift (binary)
* :white_check_mark: MessagePack (bin)
* :white_check_mark: Apache Avro (bytes and fixed for a fixed-length byte array)
* :white_check_mark: BSON (binary data)
* :white_check_mark: Smile (binary)
* :white_check_mark: Microsoft Bond (blob)
* :x: UBJSON
* :grey_question: TOML
* :white_check_mark: CapnProto (data)
* :grey_question: Apache Parquet
* :white_check_mark: CBOR (byte string)
* :x: FlatBuffers
* :white_check_mark: FlexBuffers (blob)

## Arbitrary-precision Decimal Values

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :grey_question: XML
* :x: Protocol Buffers
* :grey_question: YAML
* :x: Facebook Thrift
* :x: MessagePack
* :white_check_mark: Apache Avro ([Arbitrary-precision Two’s Complement signed decimal numbers](https://avro.apache.org/docs/1.12.0/specification/#decimal))
* :x: BSON
* :white_check_mark: Smile
* :x: Microsoft Bond
* :white_check_mark: UBJSON
* :grey_question: TOML
* :x: CapnProto
* :grey_question: Apache Parquet
* :white_check_mark: CBOR ([Arbitrary-precision signed decimals (mantissa and scale-based)](https://www.rfc-editor.org/rfc/rfc7049#section-2.4.3))
* :x: FlatBuffers
* :x: FlexBuffers

## Numeric

### ASN.1

* Big Endian Two’s Complement signed integers of user-defined length
* Big Endian unsigned integers of user-defined length
* Real numbers consisting of up to 255 bytes encoding the base, scale, exponent, and mantissa
* Arbitrary-length ASCII-encoded decimal numbers

### JSON

* Arbitrary-precision ASCII-encoded numbers

### XML

* TODO

### Protocol Buffers

* 32-bit and 64-bit Two’s Complement Little Endian Base 128 (LEB128) variable-length signed integers
* 32-bit and 64-bit Little Endian Base 128 (LEB128) variable-length unsigned integers
* 32-bit and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers
* Little Endian 32-bit and 64-bit fixed-length unsigned integers
* Little Endian 32-bit and 64-bit fixed-length Two’s Complement signed integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### YAML

* TODO

### Facebook Thrift

* 16-bit, 32-bit, and 64-bit ZigZag-encoded Little Endian Base 128 variable-length signed integers
* Little Endian 64-bit IEEE 764 floating-point numbers

### MessagePack

* Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Big Endian 7-bit, 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### Apache Avro

* 32-bit and 64-bit ZigZag-encoded Little Endian Base 128 (LEB128) variable-length integers
* Arbitrary-precision Two’s Complement signed decimal numbers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### BSON

* Little Endian Two’s Complement signed 32-bit and 64-bit integers
* Little Endian unsigned 64-bit integers
* Little Endian 64-bit and 128-bit IEEE 764 floating-point numbers

### Smile

* 5-bit, 32-bit, and 64-bit ZigZag-encoded signed Little Endian Base 128 (LEB128) variable-length integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers encoded using 7 bit groups
* Arbitrary-length stringified signed integers
* Arbitrary-precision decimals (with scale and stringified integral)

### Microsoft Bond

* 16-bit, 32-bit, and 64-bit Little Endian Base 128 (LEB128) variable-length unsigned integers
* 16-bit, 32-bit, and 64-bit ZigZag-encoded (4.2) Little Endian Base 128 (LEB128) variable-length signed integers
* Fixed-length 8-bit unsigned integers
* Fixed-length 8-bit Two’s Complement signed integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### UBJSON

* Big Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Big Endian 8-bit unsigned integers
* Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers
* Arbitrary-precision ASCII-encoded numbers

### TOML

TODO

### CapnProto

* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### Apache Parquet

TODO

### CBOR

* Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big unsigned integers
* Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-big negative integers (encoded as−1 minus the value)
* Big Endian 32-bit and 64-bit IEEE 764 floating-point numbers
* Big Endian arbitrary-length positive and negative integers
* Arbitrary-precision signed decimals (mantissa and scale-based)

### FlatBuffers

* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 32-bit and 64-bit IEEE 764 floating-point numbers

### FlexBuffers

* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers
* Little Endian 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers
* Little Endian 16-bit, 32-bit, and 64-bit IEEE 764 floating-point numbers

## Date/Time/Duration

* :white_check_mark: ASN.1 (Date, Time and Date-time)
* :x: JSON
* :grey_question: XML
* :white_check_mark: Protocol Buffers (Timestamp, Duration)
* :grey_question: YAML
* :x: Facebook Thrift
* :white_check_mark: MessagePack (32-bit, 64-bit, and 96-bit UNIX seconds and nanoseconds Epoch timestamps)
* :white_check_mark: Apache Avro
  + Date (days from the UNIX Epoch)
  + Time (milliseconds and microseconds)
  + Timestamp (milliseconds and microseconds)
  + Duration
* :white_check_mark: BSON (MongoDB Timestamp)
* :x: Smile
* :x: Microsoft Bond (also Little Endian UTF-16)
* :x: UBJSON
* :grey_question: TOML
* :x: CapnProto
* :grey_question: Apache Parquet
* :white_check_mark: CBOR (Datetime, Epoch)
* :x: FlatBuffers
* :x: FlexBuffers

## Choice

ASN.1

## Enum

ASN.1, Protocol Buffers, Thrift, Apache Avro, CapnProto, FlatBuffers

## Set

ASN.1, Thrift, Bond

## Sequence

ASN.1

## Array

JSON, MessagePack, BSON, Avro, BSON, Smile, UBJSON, CBOR, FlatBuffers, 

## Object

JSON, BSON, Smile, UBJSON

## List

Protocol Buffers, Thrift, Bond, CapnProto

## Map

Protocol Buffers, Thrift, MessagePack, Avro, CBOR, FlexBuffers

## Message

Protocol Buffers

## Oneof

Protocol Buffers

## Struct

Protocol Buffers, Thrift, Bond, CapnProto, FlatBuffers

## Union

Thrift, Avro, CapnProto, FlatBuffers

## Record

Avro

## Maybe

Bond

## Nullable

Bond

## Vector

Bond, FlatBuffers, FlexBuffers

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