# C

## Int64

> int64_t	Signed	64	8	−2^63 which equals −9,223,372,036,854,775,808	2^63 − 1 which equals 9,223,372,036,854,775,807

## Float64

> GNU C uses the floating-point representations specified by the IEEE 754-2008 Standard for Floating-Point Arithmetic.

> Standard C floating-point types follow IEEE 754 specifications (where supported): float: 32-bit single precision (24-bit mantissa), double: 64-bit double precision (53-bit mantissa),  long double: Implementation-dependent (80-bit on x86)

## Decimal

arbitraire:

> An arbitrary precision mathematics library. 

## Time

### Bnz-0/rfc3339timestamp

Seems there is a third-party library that supports parsing RFC 3339
https://github.com/Bnz-0/rfc3339timestamp

```c
#include <stdio.h>
#define RFC3339_IMPL
#include "rfc3339.h"

int main() {
	const char* str = "2024-05-01T10:47:40.123456+01:00";
	rfc3339time t = {0};
	rfc3339time_parse(str, &t);
	printf("Unix timestamp: %ld\n", rfc3339time_as_secs(&t));
	printf("Unix timestamp (microseconds): %ld\n", rfc3339time_as_us(&t));
	return 0;
}
```

Thanks to Matteo Benzi for providing this example that parses RFC 3339 up to microseconds:

```c
#include <stdio.h>
#define RFC3339_IMPL
#include "rfc3339.h"

int main() {
    rfc3339time t = {0};
    char outstr[50] = {0};
    rfc3339time_parse("2021-10-08T02:00:01.218456789+05:00", &t);
    rfc3339time_fmt(outstr, sizeof(outstr), &t);
    printf("%s\n", outstr);

    return 0;
}
```

https://github.com/Bnz-0/rfc3339timestamp/issues/2#issuecomment-3012362789

After enquiring this library now also supports nanoseconds:

https://github.com/Bnz-0/rfc3339timestamp/issues/3#issuecomment-3090755150

Thank you Matteo Benzi 

### ianjray/rfc3339

After [enquiring](https://github.com/ianjray/rfc3339/issues/1) with various C libraries one decided to implement rfc3339 parsing with nanoseconds

https://github.com/ianjray/rfc3339/commit/843a505f18bce5c2d134cbd11d027877c12b7c48

Thank you github user: ianjray

## Char

> The char data type is used to store a single character.

## References

* [C library that supports parsing RFC 3339](https://github.com/Bnz-0/rfc3339timestamp/issues/2)
* [Asked on Stackoverflow](https://stackoverflow.com/questions/79680826/is-there-a-library-to-parse-time-rfc-3339-in-pure-c?noredirect=1#comment140544984_79680826)
* [arbitraire](https://github.com/hlibc/arbitraire)
* [Floating Representations](https://www.gnu.org/software/c-intro-and-ref/manual/html_node/Floating-Representations.html)
* [C Floating-Point Types](https://www.zetcode.com/clang/float-type/)
* [C Programming/stdint.h](https://en.wikibooks.org/wiki/C_Programming/stdint.h)
* [C Character Data Types](https://www.w3schools.com/c/c_data_types_characters.php)
* [C library that supportfs RFC3339 parsing with nanoseconds](https://github.com/ianjray/rfc3339/commit/843a505f18bce5c2d134cbd11d027877c12b7c48)