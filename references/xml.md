# XML

Each XML element has unordered attributes, which can be modeled as a Object followed by an ordered List of elements.

## Basic Types

* [xsi:nil](https://www.w3.org/TR/xmlschema-1/#xsi_nil)
* boolean (XML Schema)

## String Types

* string
* normalizedString
* text
* token
* whitespace
* TEXT_NODE
* COMMENT_NODE

## Byte Array Types

* hexBinary
* base64Binary

## Decimal Types

* decimal (A decimal value)
* integer (An integer value)
* nonPositiveInteger (An integer containing only non-positive values (..,-2,-1,0))
* negativeInteger (An integer containing only negative values (..,-2,-1))
* nonNegativeInteger (An integer containing only non-negative values (0,1,2,..))
* positiveInteger (An integer containing only positive values (1,2,..))

## Float64 Types

* float (float is patterned after the IEEE single-precision 32-bit floating point type [IEEE 754-1985].)
* double (The double datatype is patterned after the IEEE double-precision 64-bit floating point type [IEEE 754-1985].)

## Uint64 Types

* unsignedLong (An unsigned 64-bit integer)
* unsignedInt (An unsigned 32-bit integer)
* unsignedShort (An unsigned 16-bit integer)
* unsignedByte (An unsigned 8-bit integer)

## Int64 Types

* long (A signed 64-bit integer)
* int (A signed 32-bit integer)
* short (A signed 16-bit integer)
* byte (A signed 8-bit integer)

## Date Types

* date
* gYearMonth
* gYear
* gMonthDay
* gDay
* gMonth

## Timestamp Types

* dateTime
* time

## Duration Types

* duration

## Enum Types

* xs:enumeration

## List Types

* element
* ELEMENT_NODE

## Referenced

### XML Schema

* boolean
* string
* normalizedString
* hexBinary
* base64Binary
* decimal (A decimal value)
* integer (An integer value)
* nonNegativeInteger (An integer containing only non-negative values (0,1,2,..))
* nonPositiveInteger (An integer containing only non-positive values (..,-2,-1,0))
* negativeInteger (An integer containing only negative values (..,-2,-1))
* positiveInteger (An integer containing only positive values (1,2,..))
* float
* double
* unsignedLong (An unsigned 64-bit integer)
* unsignedInt (An unsigned 32-bit integer)
* unsignedShort (An unsigned 16-bit integer)
* unsignedByte (An unsigned 8-bit integer)
* long (A signed 64-bit integer)
* int (A signed 32-bit integer)
* short (A signed 16-bit integer)
* byte (A signed 8-bit integer)
* date
* gYearMonth
* gYear
* gMonthDay
* gDay
* gMonth
* dateTime
* time
* duration
* anyURI
* QName
* NOTATION
* token
* language
* NMTOKEN
* NMTOKENS
* Name
* NCName
* ID
* IDREF
* IDREFS
* ENTITY
* ENTITIES
* xs:enumeration

### DOM

* TEXT_NODE
* COMMENT_NODE
* ELEMENT_NODE
* ATTRIBUTE_NODE
* CDATA_SECTION_NODE
* ENTITY_REFERENCE_NODE
* ENTITY_NODE
* PROCESSING_INSTRUCTION_NODE
* DOCUMENT_NODE
* DOCUMENT_TYPE_NODE
* DOCUMENT_FRAGMENT_NODE
* NOTATION_NODE
* ShadowRoot

### RelaxNG

* empty
* text
* token
* whitespace
* element
* attribute
* group
* interleave
* choice
* optional
* zeroOrMore
* oneOrMOre
* list
* mixed
* ref
* parentRef
* value
* data
* notAllowed
* externalRef
* except

### DTD

* CDATA
* ENTITY
* ENTITIES
* DTD ID
* IDREF
* IDREFS
* NMTOKEN
* NMTOKENS
* PCDATA

### References

* https://www.liquid-technologies.com/Reference/Glossary/DTD_Datatypes_index.html
* https://relaxng.org/spec-20011203.html#full-syntax
* https://dom.spec.whatwg.org/#node-trees
* https://www.w3schools.com/xml/dom_nodetype.asp
* https://www.w3.org/TR/xmlschema-2/#built-in-derived
* https://www.w3.org/TR/xmlschema-2/#built-in-primitive-datatypes
* https://www.w3schools.com/xml/schema_dtypes_numeric.asp
* https://www.w3schools.com/XML/schema_facets.asp