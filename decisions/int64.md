# Int64

An Int64 is a range from:
MIN: -1 * 2^63 = -9,223,372,036,854,775,808
MAX: 2^63 - 1  =  9,223,372,036,854,775,807

Every serialization format we [surveyed](./survey/Readme.md) supports double-precision integers.

The interface already includes a `Float64` type.
The `Float64` type can precisely represent integers between −2^53 to 2^53.
Integers outside of this range is not very popular, but there is a fallback token kind called `Decimal` that can represent even larger number precisely.

There is no evidence that on modern processors `Float64` comparisons are slower than `Int64` comparisons.

This means including an extra `Int64` base type is not necessary and we can simplify the interface by not including it.

However the interface also supports the `Nanoseconds` `Kind` with an `Int64` value. Precisely representing nanoseconds up to 2^53 might be enough for durations, but is not enough to represent time since the epoch, as it only represents 1 January 1970 to about 15 April 1970, so only 3 and a half months, instead of 292 years.

## References

> Integers from −2^53 to 2^53 (−9,007,199,254,740,992 to 9,007,199,254,740,992) can be exactly represented - https://en.wikipedia.org/wiki/Double-precision_floating-point_format#Precision_limitations_on_integer_values

> Additionally, if you profile a modern CPU, in high performance code when you are trying to get all the performance you can, you will find that because integer and floating units are separate hardware, the integer ALU is easy to saturate because it is often being used to compute all the mundane things you might take for granted...such as computing the math to increment your loop counter in a for-loop and computing the memory address offsets to access different adjacent slots in an array. If you do all your interesting work in fixed point, you will saturate your ALU while your FPU is sitting idle. - https://www.reddit.com/r/C_Programming/comments/12s8ede/is_there_any_performance_benefit_to_using_int_vs/