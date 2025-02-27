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

## Decimal Types

* REAL (Real numbers consisting of up to 255 bytes encoding the base, scale, exponent, and mantissa and Arbitrary-length ASCII-encoded decimal numbers)
* NumericString

## Float64 Types

* REAL (Real numbers consisting of up to 255 bytes encoding the base, scale, exponent, and mantissa and Arbitrary-length ASCII-encoded decimal numbers)

## Int64 Types

* INTEGER (Big Endian Two’s Complement signed integers of user-defined length)

## Referenced

### Generics

* NULL
* BOOLEAN
* UTF8String
* OCTET STRING
* REAL (Real numbers consisting of up to 255 bytes encoding the base, scale, exponent, and mantissa and Arbitrary-length ASCII-encoded decimal numbers)
* INTEGER (Big Endian Two’s Complement signed integers of user-defined length)
* BIT STRING
* OBJECT IDENTIFIER
* ENUMERATED

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

* TIME
* UTCTime
* GeneralizedTime
* DATE
* TIME-OF-DAY
* DATE-TIME
* DURATION

### References

* https://www.oss.com/asn1/resources/asn1-made-simple/asn1-quick-reference.html
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"