# Python

## Int64

> Integers have unlimited precision.

## Float64

> Floating-point numbers are usually implemented using double in C; information about the precision and internal representation of floating-point numbers for the machine on which your program is running is available in sys.float_info.

## Decimal

> Unlike hardware based binary floating point, the decimal module has a user alterable precision

## Time

Python's datetime library has no support for nanoseconds.

> Popular Python libraries don’t do much more with a lack of an intermediate format and simply truncate the trailing digits.

This includes libraries such as pendulum and ciso8601.

> If you want a higher resolution you’ll have to use NumPy’s datetime64.

```python
import numpy
numpy.datetime64('2016-06-10T21:42:24.76073899')
# numpy.datetime64('2016-06-10T21:42:24.760738990+0000')
# Created a datetime with nanosecond resolution
```

But `datetime64` does not handle timezones, so does not comply with RFC 3339.

Nanoseconds are only supported by a different third-party library: `proto.datetime_helpers.DatetimeWithNanoseconds`'s `from_rfc3339` method handles both nanoseconds and RFC 3339.

## References

* [ISO 8601 and Nanosecond Precision Across Languages](https://nickb.dev/blog/iso8601-and-nanosecond-precision-across-languages/)
* [Proto DateTime Helpers](https://proto-plus-python.readthedocs.io/en/latest/reference/datetime_helpers.html)
* [Numeric Types — int, float, complex](https://docs.python.org/3/library/stdtypes.html#typesnumeric)
* [decimal](https://docs.python.org/3/library/decimal.html)
* [datetime module has no support for nanoseconds](https://github.com/python/cpython/issues/59648)