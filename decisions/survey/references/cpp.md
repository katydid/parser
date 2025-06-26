# C++

## Int64

`int64_t`

> The former is a signed integer type with exactly 64 bits.

## Float64



## Decimal

**TODO: Boost.Multiprecision Standard double isn’t precise; use multiprecision libs.**

## Time

Thanks to Arne Haak for providing this example of parsing RFC 3339 with nanoseconds

```cpp
#include <chrono>
#include <iostream>
#include <sstream>

int
main()
{
    std::chrono::sys_time<std::chrono::nanoseconds> timestamp;
    std::stringstream ss{"2021-10-08T02:00:01.218456789+05:00"};
    ss >> std::chrono::parse("%FT%T%Z", timestamp);
    std::cout << timestamp << '\n';
}
```

Thanks to Howard E. Hinnant for providing this example of RFC 9557

```cpp
#include <chrono>
#include <format>
#include <iostream>
#include <sstream>

int
main()
{
    using namespace std;
    using namespace chrono;
    istringstream in{"2022-07-08T00:14:07+01:00[Europe/Paris]"};
    sys_seconds tp;
    string tz_name;
    in >> parse("%FT%T%Ez[%Z]", tp, tz_name);
    cout << tz_name << '\n';
    cout << format("{:%F %T %Z}", tp) << '\n';
    zoned_time zt{tz_name, tp};
    cout << format("{:%F %T %Z}", zt) << '\n';
    cout << zt.get_info().offset << '\n';
}
```

Output:

```
Europe/Paris
2022-07-07 23:14:07 UTC
2022-07-08 01:14:07 CEST
7200s
```

### Previous Attempts

> For parsing and comparing RFC3339 formated dates, you can use Howard Hinnant's date library.

```cpp
#include "date/date.h"
#include <iostream>
#include <sstream>

int main()
{
    using namespace date;
    std::istringstream infile{"2005-08-15T15:52:01+04:00"};
    sys_seconds tp;  // This is a system_clock time_point with seconds precision
    infile >> parse("%FT%T%Ez", tp);
    std::cout << tp.time_since_epoch() << " is " << tp << '\n';
}
```

> A slightly modified versions of "date.h" and "tz.h" were voted into the C++20 working draft.

The author of the library confirmed that this should work:

```cpp
#include "date/date.h"
include <chrono>
include <iostream>
include <sstream>
int main()
{
    using namespace date;
    using namespace std;
    using namespace std::chrono;

    istringstream in{"2021-10-08T02:00:01.218456789Z"};
    in.exceptions(ios::failbit);
    sys_time<nanoseconds> tp;
    in >> parse("%FT%TZ", tp);
    cout << tp << " = " << tp.time_since_epoch() << '\n';
}

Output = 
2021-10-08 02:00:01.218456789 = ...ns
```

## References

* [Nanoseconds & RFC3339 Timestamp C++](https://gist.github.com/Ujang360/4a52f736b59be4724f6db4ebfeaf1413)
* [HowardHinnant's date library](https://github.com/HowardHinnant/date)
* [Stack Overflow: Parsing RFC3339 dates in C++](https://stackoverflow.com/questions/3091804/parsing-rfc3339-dates-in-c)
* [Reddit: How to parse RFC3339 time into uint64_t milliseconds since epoch?](https://www.reddit.com/r/cpp_questions/comments/o3h9i9/how_to_parse_rfc3339_time_into_uint64_t/)
* [HowardHinnant's Unit Test with some basic nanosecond test](https://github.com/HowardHinnant/date/blob/6d7739e7e8e8864dc5eb79e42b6c2675cd7733ca/test/date_test/make_time.pass.cpp#L42-L50)
* [Stack Overflow: Definition of Int64](https://stackoverflow.com/questions/13604137/definition-of-int64-t#13604190)
* [Godbolt playground](https://gcc.godbolt.org/z/z5n5KGKrs)