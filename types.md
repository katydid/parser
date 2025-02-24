# Types supported by each serialization format

## TODO

* XML
* YAML
* TOML
* Apache Parquet

## Undefined

`undefined` is only supported by BSON where it is deprecated and in CBOR where it is substitute for a data item with an encoding problem.

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