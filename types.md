# Types supported by each serialization format

## Undefined

`undefined` is only supported by BSON where it is deprecated and in CBOR where it is substitute for a data item with an encoding problem.

## Null

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :grey_question: XML
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


