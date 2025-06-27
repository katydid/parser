# Erlang

## Int64

**TODO**

## Float64

> Please also note that Erlang's floats do not exactly match IEEE 754 floats, in that neither Inf nor NaN are supported in Erlang. Any operation that would result in NaN, +Inf, or -Inf, will instead raise a badarith exception.

## Decimal

**TODO**

## Time

```erlang
main(_) ->
    %% Correct RFC 3339 format with 'T' between date and time
    TimeStr = "2018-02-01T16:17:58.123456789+01:00",

    %% Convert to system time in nanoseconds
    case calendar:rfc3339_to_system_time(TimeStr, [{unit, nanosecond}]) of
        SystemTime when is_integer(SystemTime) ->
            io:format("System time (nanoseconds since Unix epoch): ~p~n", [SystemTime]);
        {error, Reason} ->
            io:format("Failed to parse RFC3339 time: ~p~n", [Reason])
    end.
```

```
$ System time (nanoseconds since Unix epoch): 1517498278123456789
```

## Char

> $char: ASCII value or unicode code-point of the character char.

```erlang
> $\n.
10
```

## References

* [Erlang Data Types](https://erlang.org/documentation/doc-15.0-rc1/doc/system/data_types.html)
* [Erlang Playground Testing out parsing code](https://www.mycompiler.io/view/A7Lq1y0D6nR)
* [Erlang calendar](https://www.erlang.org/doc/apps/stdlib/calendar.html#rfc3339_to_system_time/2)
* [Erlang Data Types](https://www.erlang.org/doc/system/data_types.html#number)