# Lean

## Time

Thank you to Markus Himmel

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

> Regarding your second question, at the moment we only parse either an offset or a time zone identifier. So you can write zoned("2022-07-08T00:14:07+01:00") to get a ZonedDateTime, or you can write zoned("2022-07-08T00:14:07[Europe/Paris]") which returns an IO ZonedDateTime that will look up the offset in the computer's time zone database.

## Reference

* [Zulip Chat](https://leanprover.zulipchat.com/#narrow/channel/113488-general/topic/parsing.20DateTime.20in.20format.20RFC.203339.20including.20nanoseconds/with/525924778.01)