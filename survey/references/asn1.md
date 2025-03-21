# ASN.1

## Basic Types

* NULL
* BOOLEAN

## String Types

* UTF8String
* PrintableString
* IA5String
* VisibleString
* GeneralString
* GraphicString
* UniversalString
* CHARACTER STRING
* BMPString
* TeletexString, T61String
* VideotexString

## Byte Array Types

* OCTET STRING
* BIT STRING (Arbitrary-length bit array)

## Decimal Types

* REAL (Real numbers consisting of up to 255 bytes encoding the base, scale, exponent, and mantissa and Arbitrary-length ASCII-encoded decimal numbers)
* NumericString

## Float64 Types

* REAL (Real numbers consisting of up to 255 bytes encoding the base, scale, exponent, and mantissa and Arbitrary-length ASCII-encoded decimal numbers)

## Int64 Types

* INTEGER (Big Endian Two’s Complement signed integers of user-defined length)

## Date Types

* DATE

## Timestamp Types

* TIME
* UTCTime
* GeneralizedTime
* TIME-OF-DAY
* DATE-TIME

## Duration Types

* DURATION

## Enum Types

* ENUMERATED

## List Types

* SEQUENCE OF
* OBJECT IDENTIFIER (list of integers)

## Set Types

* SET OF

## Union Types

* CHOICE

## Object Types

* SET (fields in any order)
* SEQUENCE (fields in order)

## Referenced

### Generics

* NULL
* BOOLEAN
* UTF8String
* OCTET STRING
* REAL (Real numbers consisting of up to 255 bytes encoding the base, scale, exponent, and mantissa and Arbitrary-length ASCII-encoded decimal numbers)
* INTEGER (Big Endian Two’s Complement signed integers of user-defined length)
* ENUMERATED
* BIT STRING
* OBJECT IDENTIFIER (an object identifier, which is a sequence of integer components that identify an object such as an algorithm or attribute type.  components can generally have any nonnegative value. This type is a non-string type. For example { 1 2 840 113549 } = RSA Data Security, Inc. { 1 2 840 113549 1 } = RSA Data Security, Inc. PKCS)

### Strings

* UTF8String
* NumericString
* PrintableString
* IA5String
* VisibleString
* GeneralString
* GraphicString
* UniversalString
* CHARACTER STRING
* BMPString
* TeletexString, T61String
* VideotexString

### Composites

* SEQUENCE
* SEQUENCE OF
* SET
* SET OF
* CHOICE

### Times

* DATE
* TIME
* UTCTime
* GeneralizedTime
* TIME-OF-DAY
* DATE-TIME
* DURATION

### References

* https://www.oss.com/asn1/resources/asn1-made-simple/asn1-quick-reference.html
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"
* https://www.oss.com/asn1/resources/asn1-made-simple/asn1-quick-reference/enumerated.html
* https://www.oss.com/asn1/resources/asn1-made-simple/asn1-quick-reference/set.html
* https://www.oss.com/asn1/resources/asn1-made-simple/asn1-quick-reference/sequenceof.html
* https://www.oss.com/asn1/resources/asn1-made-simple/asn1-quick-reference/sequence.html
* https://www.oss.com/asn1/resources/asn1-made-simple/asn1-quick-reference/set.html
* https://luca.ntop.org/Teaching/Appunti/asn1.html