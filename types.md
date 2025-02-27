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
* :x: Parquet
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
* :x: Parquet
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
* :x: Parquet
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

## Struct / Message / Record / Object / Tables

Different from maps, these fields/keys are all of type string.

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