# Time

There are two kinds to represent time and duration:

* '9': Nanoseconds (Int64) (used for duration and time since epoch)
* 'T': Date Time ISO 8601 (String)

In many serialization formats an integer is used to encode the time or duration.
There is usually confusion about which unit of time is selected, so conforming on one is important.

Nanoseconds is the most precise measurement we have right now.

Int64 provides enough space for 292 years, which is enough for any practical duration and any practical date, since the epoch (1970 January 1).

For other dates like birthdays that fall outside of the range, we propose using Date Time ISO 8601 with RFC3339: YYYY-MM-DDTHH:MM:SS.sssssssssZ.

The times should always be normalized to UTC timezone `Z`.

RFC3339 is a Internet profile of the ISO 8601.
IETF RFC 3339 defines a profile of ISO 8601 for use in Internet protocols and standards.
It clears up some confusion left in ISO 8601 including timezone that is offset against UTC.

RFC 9557 extends RFC3339 with named timezones, so that daylight savings time can be taken into account. 
The interface sticks to the older RFC3339 and also limits the timezone to UTC to avoid the complications of daylight savings time.

## Programming Language Support

**TODO**

## ABNF

```
date-fullyear   = 4DIGIT
date-month      = 2DIGIT  ; 01-12
date-mday       = 2DIGIT  ; 01-28, 01-29, 01-30, 01-31 based on
                            ; month/year
time-hour       = 2DIGIT  ; 00-23
time-minute     = 2DIGIT  ; 00-59
time-second     = 2DIGIT  ; 00-58, 00-59, 00-60 based on leap second
                            ; rules
time-secfrac    = "." 1*DIGIT
time-numoffset  = ("+" / "-") time-hour ":" time-minute
time-offset     = "z" / "Z" / time-numoffset

partial-time    = time-hour ":" time-minute ":" time-second
                    [time-secfrac]
full-date       = date-fullyear "-" date-month "-" date-mday
full-time       = partial-time time-offset

date-time       = full-date ("t" / "T" / " ") full-time
```

## References

* [ISO 8601 and Nanosecond Precision Across Languages](https://nickb.dev/blog/iso8601-and-nanosecond-precision-across-languages/)
* [RFC3339](https://www.rfc-editor.org/rfc/rfc3339)
* [ABNF](https://www.rfc-editor.org/rfc/rfc3339#section-5.6)

GNU CoreUtils's date command has an --iso-8601 option
```
$ date -u --rfc-3339=ns
2025-02-16 10:58:44.966864492+00:00
```
- https://en.wikipedia.org/wiki/ISO_8601

```
5.3. Rarely Used Options

A format which includes rarely used options is likely to cause
interoperability problems.  This is because rarely used options are
less likely to be used in alpha or beta testing, so bugs in parsing
are less likely to be discovered.  Rarely used options should be made
mandatory or omitted for the sake of interoperability whenever
possible.

The format defined below includes only one rarely used option:
fractions of a second.  It is expected that this will be used only by
applications which require strict ordering of date/time stamps or
which have an unusual precision requirement.
```
- https://www.rfc-editor.org/rfc/rfc3339#section-5.3

> Building upon the foundations of RFC 3339, the IETF introduced the Internet Extended Date/Time Format (IXDTF) in RFC 9557 - https://en.wikipedia.org/wiki/ISO_8601#RFCs

