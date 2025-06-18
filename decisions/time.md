# Time

There are two kinds to represent time and duration:

* '9': Nanoseconds (Int64) (used for duration and time since epoch)
* 'T': Date Time ISO 8601 (String)

In many serialization formats an integer is used to encode the time or duration.
There is usually confusion about which unit of time is selected, so conforming on one is important.

Nanoseconds is the most precise measurement we have right now.

Int64 provides enough space for 292 years, which is enough for any practical duration and any practical date, since the epoch (1970 January 1).

For other dates like birthdays that fall outside of the range, we propose using Date Time ISO 8601: YYYY-MM-DDTHH:MM:SS.