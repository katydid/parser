# Types supported by each serialization format

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

## Byte Array

* :white_check_mark: ASN.1
* :x: JSON (possible with base64 encoding)
* :white_check_mark: XML
* :white_check_mark: Protobufs
* :white_check_mark: YAML
* :white_check_mark: Thrift
* :white_check_mark: MsgPack
* :white_check_mark: Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :white_check_mark: UBJSON
* :x: TOML
* :white_check_mark: CapnProto
* :white_check_mark: Parquet
* :white_check_mark: CBOR
* :white_check_mark: FlatBuffers
* :white_check_mark: FlexBuffers

## Arbitrary-precision Decimal Values (decimal)

`decimal` includes integers and floats outside the 64-bit range.
These are numbers that are tough to represent with built-in types in most programming languages.

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :white_check_mark: XML
* :x: Protobufs
* :white_check_mark: YAML
* :x: Thrift
* :x: MsgPack
* :white_check_mark: Avro
* :white_check_mark: BSON
* :white_check_mark: Smile
* :white_check_mark: UBJSON
* :x: TOML
* :x: CapnProto
* :white_check_mark: Parquet (96 bit signed ints)
* :white_check_mark: CBOR
* :x: FlatBuffers
* :x: FlexBuffers

## Float64

Double-precision floating-point format IEEE-754

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

## Uint64

* :x: ASN.1
* :x: JSON
* :white_check_mark: XML
* :white_check_mark: Protobufs
* :x: YAML
* :x: Thrift
* :white_check_mark: MsgPack
* :x: Avro
* :x: BSON
* :x: Smile
* :x: UBJSON
* :x: TOML
* :white_check_mark: CapnProto
* :x: Parquet
* :white_check_mark: CBOR
* :white_check_mark: FlatBuffers
* :white_check_mark: FlexBuffers

## Int64

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

## Date

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :white_check_mark: XML
* :x: Protobufs
* :x: YAML
* :x: Thrift
* :x: MsgPack
* :white_check_mark: Avro
* :white_check_mark: BSON
* :x: Smile
* :x: UBJSON
* :white_check_mark: TOML
* :x: CapnProto
* :white_check_mark: Parquet
* :white_check_mark: CBOR
* :x: FlatBuffers
* :x: FlexBuffers

## Timestamp

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :white_check_mark: XML
* :white_check_mark: Protobufs
* :white_check_mark: YAML
* :x: Thrift
* :white_check_mark: MsgPack
* :white_check_mark: Avro
* :white_check_mark: BSON
* :x: Smile
* :x: UBJSON
* :white_check_mark: TOML
* :x: CapnProto
* :white_check_mark: Parquet
* :white_check_mark: CBOR
* :x: FlatBuffers
* :x: FlexBuffers

## Duration

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :white_check_mark: XML
* :white_check_mark: Protobufs
* :x: YAML
* :x: Thrift
* :white_check_mark: MsgPack
* :white_check_mark: Avro
* :x: BSON
* :x: Smile
* :x: UBJSON
* :x: TOML
* :x: CapnProto
* :x: Parquet
* :x: CBOR
* :x: FlatBuffers
* :x: FlexBuffers

## Enum

* :white_check_mark: ASN.1
* :x: JSON
* :white_check_mark: XML
* :white_check_mark: Protobufs
* :x: YAML
* :white_check_mark: Thrift
* :x: MsgPack
* :white_check_mark: Avro
* :x: BSON
* :x: Smile
* :x: UBJSON
* :x: TOML
* :white_check_mark: CapnProto
* :white_check_mark: Parquet
* :x: CBOR
* :white_check_mark: FlatBuffers
* :x: FlexBuffers

## List

Also referred to as Sequence, Array, Vector, repeated or elements.

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

## Set

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :x: XML
* :x: Protobufs
* :white_check_mark: YAML
* :white_check_mark: Thrift
* :x: MsgPack
* :x: Avro
* :x: BSON
* :x: Smile
* :x: UBJSON
* :x: TOML
* :x: CapnProto
* :x: Parquet
* :x: CBOR
* :x: FlatBuffers
* :x: FlexBuffers

## Union

Also referred to as Oneof or Choice.

* :white_check_mark: ASN.1
* :white_check_mark: JSON
* :white_check_mark: XML
* :white_check_mark: Protobufs
* :x: YAML
* :white_check_mark: Thrift
* :x: MsgPack
* :white_check_mark: Avro
* :x: BSON
* :x: Smile
* :x: UBJSON
* :x: TOML
* :white_check_mark: CapnProto
* :x: Parquet
* :x: CBOR
* :white_check_mark: FlatBuffers
* :x: FlexBuffers

## Map

Maps are key-value pairs, where the keys are not limited to strings.

* :x: ASN.1
* :x: JSON
* :x: XML
* :white_check_mark: Protobufs
* :white_check_mark: YAML
* :white_check_mark: Thrift
* :white_check_mark: MsgPack
* :x: Avro
* :x: BSON
* :x: Smile
* :x: UBJSON
* :x: TOML
* :x: CapnProto
* :white_check_mark: Parquet
* :white_check_mark: CBOR
* :x: FlatBuffers
* :white_check_mark: FlexBuffers

## Object

Also referred to as Struct, Message, Record, Object or Table.
These are key-value pairs, where the keys are limited to strings.

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
