# Javascript

## Int64

BigInt supports arbitrary precision integers

## Float64

> In JavaScript, Number is a numeric data type in the double-precision 64-bit floating point format (IEEE 754)

## Decimal

**TODO: Use decimal.js or Big.js Native Number uses 64-bit float; use libraries for precision.**

## Time

Seems as though Date.parse supports RFC 3339

> Date.parse("2025-06-24T16:49:32.123456789+02:00");

jsjoda's OffsetDateTime seems to support RFC 3337

> A date-time with an offset from UTC/Greenwich in the ISO-8601 calendar system, such as 2007-12-23T10:15:30+01:00.

It also includes a nano method

> public nano(): number

We found a test in jsjoda for parsing nanoseconds with OffsetDateTime

> OffsetDateTime.parse('2020-01-02T03:04:05.000000006+07:00');

Seems Javascript is planning support for RFC 9557:

> The abstract operation ParseISODateTime takes arguments isoString (a String) and allowedFormats (a List of nonterminals) and returns either a normal completion containing an ISO Date-Time Parse Record or a throw completion. It parses the argument as an ISO 8601 / RFC 9557 string and returns a Record representing each date and time component as a distinct field.

jsjoda's ZonedDateTime seems to support RFC 9557 already:

> public static parse(text: string, formatter: DateTimeFormatter): ZonedDateTime Obtains an instance of ZonedDateTime from a text string such as 2007-12-03T10:15:30+01:00[Europe/Paris].

## References

* [BigInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt)
* [bigint](https://developer.mozilla.org/en-US/docs/Glossary/BigInt)
* [Number](https://developer.mozilla.org/en-US/docs/Glossary/Number)
* [Date.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/parse)
* [jsjoda OffsetDateTime](https://js-joda.github.io/js-joda/class/packages/core/src/OffsetDateTime.js~OffsetDateTime.html)
* [jsjoda test parsing nanoseconds with OffsetDateTime](https://github.com/js-joda/js-joda/blob/52de68e9fe4e51b2191a2d2ebfe187bee8b9fdc8/packages/core/test/OffsetDateTimeTest.js#L265)
* [jsjoda ZonedDateTime](https://js-joda.github.io/js-joda/class/packages/core/src/ZonedDateTime.js~ZonedDateTime.html)
* [Proposal proposal-temporal Stage 3 Draft / June 23, 2025](https://tc39.es/proposal-temporal/#sec-temporal-parseisodatetime)