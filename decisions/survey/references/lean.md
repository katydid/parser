# Lean

## Int64

> The smallest number that Int64 can represent: -2^63 = -9223372036854775808.

> The largest number that Int64 can represent: 2^63 - 1 = 9223372036854775807.

## Float64

> Float corresponds to the IEEE 754 binary64 format (double in C or f64 in Rust).

## Decimal

**TODO**

## Time

Thank you to Markus Himmel for providing an example of parsing RFC 3339

```
import Std.Time
open Std.Time.ZonedDateTime

def a := zoned("2025-06-24T16:49:32.123456789Z")
#print a

def a : Std.Time.ZonedDateTime :=
ofPlainDateTime
  {
    date :=
      Std.Time.PlainDate.ofYearMonthDayClip (Int.ofNat 2025)
        (Std.Time.Internal.Bounded.LE.ofNatWrapping (Int.ofNat 6) a._proof_1)
        (Std.Time.Internal.Bounded.LE.ofNatWrapping (Int.ofNat 24) a._proof_2),
    time :=
      { hour := Std.Time.Internal.Bounded.LE.ofNatWrapping (Int.ofNat 16) a._proof_3,
        minute := Std.Time.Internal.Bounded.LE.ofNatWrapping (Int.ofNat 49) a._proof_4,
        second := Std.Time.Internal.Bounded.LE.ofNatWrapping (Int.ofNat 32) a._proof_5,
        nanosecond := Std.Time.Internal.Bounded.LE.ofNatWrapping (Int.ofNat 123456789) a._proof_6 } }
  (Std.Time.TimeZone.ZoneRules.ofTimeZone
    { offset := { second := { val := Int.ofNat 0 } }, name := "+00:00", abbreviation := "+00:00", isDST := false })
```

> Regarding your second question, at the moment we only parse either an offset or a time zone identifier. So you can write zoned("2022-07-08T00:14:07+01:00") to get a ZonedDateTime, or you can write zoned("2022-07-08T00:14:07[Europe/Paris]") which returns an IO ZonedDateTime that will look up the offset in the computer's time zone database. - Mark Himmel

Thank you to Mark Himmel for providing a follow up example of parsing RFC 9557

```
import Std.Time

open Std Time

def rfc9557 : GenericFormat .any := datespec("uuuu-MM-dd'T'HH:mm:ssZZZZZ'['zzzz']'")

#eval do
  let date ← IO.ofExcept (rfc9557.parse "2022-07-08T00:14:07+01:00[Europe/Paris]")
  IO.println s!"Zone offset is {date.timezone.offset.second} seconds"
  IO.println s!"Zone name is {date.timezone.name}"
```

## Char

> Characters are represented by the type Char, which may be any Unicode scalar value.

## Bytes

> Lean's arrays are dynamic arrays, which are blocks of continuous memory with a defined capacity

> UInt8 : Type, Unsigned 8-bit integers. This type has special support in the compiler so it can be represented by an unboxed 8-bit value rather than wrapping a BitVec 8.

Looks like `Array UInt8` is represented as a sequence of bytes.

## UTF8Func

**TODO**

## UTF8Str

> While strings are UTF-8-encoded arrays of bytes.

## Reference

* [Zulip Chat](https://leanprover.zulipchat.com/#narrow/channel/113488-general/topic/parsing.20DateTime.20in.20format.20RFC.203339.20including.20nanoseconds/with/525924778.01)
* [Int64](https://lean-lang.org/doc/reference/latest//Basic-Types/Fixed-Precision-Integers/#fixed-ints)
* [Float](https://lean-lang.org/doc/reference/latest//Basic-Types/Floating-Point-Numbers/#Float)
* [Characters](https://lean-lang.org/doc/reference/latest//Basic-Types/Characters/)
* [Arrays](https://lean-lang.org/doc/reference/latest/Basic-Types/Arrays/)
* [Uint8](https://lean-lang.org/doc/reference/latest//Basic-Types/Fixed-Precision-Integers/#UInt8___ofBitVec)