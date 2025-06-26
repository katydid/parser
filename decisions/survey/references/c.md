# C



## Time

Seems there is a third-party library that supports parsing RFC 3339
https://github.com/Bnz-0/rfc3339timestamp

```
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

## References

* [C library that supports parsing RFC 3339](https://github.com/Bnz-0/rfc3339timestamp/issues/2)
* [Asked on Stackoverflow](https://stackoverflow.com/questions/79680826/is-there-a-library-to-parse-time-rfc-3339-in-pure-c?noredirect=1#comment140544984_79680826)