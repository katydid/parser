# Java

## Int64

> static long	MAX_VALUE A constant holding the maximum value a long can have, 2^63-1.
> static long	MIN_VALUE A constant holding the minimum value a long can have, -2^63.

## Float64

> double: The double data type is a double-precision 64-bit IEEE 754 floating point. 

## Decimal

BigDecimal:

> Immutable, arbitrary-precision signed decimal numbers.

## Time

Instant supports parsing nanoseconds, but it only parses RFC 3339 for the UTC timezone.

> The modern class Instant represents a moment in UTC. This class replaces java.util.Date, and uses a finer resolution of nanoseconds rather than milliseconds.

> Instant instant = Instant.parse( "2011-05-03T11:58:01Z" ) ;

> OffsetDateTime is an immutable representation of a date-time with an offset. This class stores all date and time fields, to a precision of nanoseconds, as well as the offset from UTC/Greenwich. For example, the value "2nd October 2007 at 13:45.30.123456789 +02:00" can be stored in an OffsetDateTime.

Looks like Java supports RFC 3339 via OffsetDateTime

> static OffsetDateTime	parse(CharSequence text) Obtains an instance of OffsetDateTime from a text string such as 2007-12-03T10:15:30+01:00.

Looks like Java also supports RFC 9557 via ZonedDateTime

> static ZonedDateTime	parse(CharSequence text) Obtains an instance of ZonedDateTime from a text string such as 2007-12-03T10:15:30+01:00[Europe/Paris].

## Char

> The char keyword is a data type that is used to store a single character.

```java
char myGrade = 'B';
System.out.println(myGrade);
```

## References

* [Stackoverflow: How do I parse RFC 3339 datetimes with Java?](https://stackoverflow.com/questions/6038136/how-do-i-parse-rfc-3339-datetimes-with-java)
* [Java 8: Class Instant](https://docs.oracle.com/javase/8/docs/api/java/time/Instant.html)
* [Java 8: Class OffsetDateTime](https://docs.oracle.com/javase/8/docs/api/java/time/OffsetDateTime.html#parse-java.lang.CharSequence-)
* [Java 8: Class ZonedDateTime](https://docs.oracle.com/javase/8/docs/api/java/time/ZonedDateTime.html)
* [ISO 8601 and Nanosecond Precision Across Languages](https://nickb.dev/blog/iso8601-and-nanosecond-precision-across-languages/)
* [long](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html)
* [Primitive Data Types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
* [BigDecimal](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/math/BigDecimal.html)
* [Java char Keyword](https://www.w3schools.com/java/ref_keyword_char.asp)