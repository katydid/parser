# JSON

## Basic Types

* null
* boolean

## String Types

* string
* date
* email
* idn-email
* hostname
* idn-hostname
* uri
* uri-reference
* iri
* iri-reference
* uri-template
* regex
* ipv4
* ipv6

## Decimal Types

* number (Arbitrary-precision ASCII-encoded numbers)

## Float64 Types

* number

## Int64 Types

* integer

## Date Types

* date

## Timestamp Types

* date-time
* time

## Duration Types

* duration

## List Types

* array

## Set Types

* uniqueItems

## Union Types

* oneOf

## Object Types

* object

## UUID Types

* uuid

## Referenced

### JSON

* null
* boolean
* string (The JSON specification does not dictate a specific required encoding, it does however use UTF-8 as the default encoding.)
* number
* integer
* array
* object

### JSON-Schema

* date
* date-time
* time
* duration
* email
* idn-email
* hostname
* idn-hostname
* uri
* uri-reference
* iri
* iri-reference
* uri-template
* regex
* ipv4
* ipv6
* uuid
* json-pointer
* relative-json-pointer

### Keywords

* uniqueItems
* oneOf
* maxItems
* minItems
* maxContains
* minContains
* maxProperties
* minProperties
* required
* dependentRequired
* allOf
* anyOf

### References

* https://json-schema.org/understanding-json-schema/reference/type
* https://json-schema.org/draft/2020-12/draft-bhutton-json-schema-validation-00#rfc.section.6.4.3
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"
* https://ubjson.org/type-reference/value-types/#string