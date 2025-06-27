# C



## Time

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

## References

* [C library that supports parsing RFC 3339](https://github.com/Bnz-0/rfc3339timestamp/issues/2)
* [Asked on Stackoverflow](https://stackoverflow.com/questions/79680826/is-there-a-library-to-parse-time-rfc-3339-in-pure-c?noredirect=1#comment140544984_79680826)