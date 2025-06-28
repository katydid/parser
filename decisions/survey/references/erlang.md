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

## Bytes

We infer that `binary` is a sequence of bytes, since otherwise how would they be optimized.

binary:

> While most of these functions could be implemented using the bit syntax, the functions in this module are highly optimized and are expected to either execute faster or consume less memory, or both, compared to equivalent implementations written in pure Erlang.

## UTF8Str

> A string in this module is represented by unicode:chardata/0, that is, a list of codepoints, binaries with UTF-8-encoded codepoints (UTF-8 binaries), or a mix of the two.

## UTF8Func

equal(A, B, IgnoreCase, Norm):

> If IgnoreCase is true the function does casefolding on the fly before the equality test.

> If Norm is not none the function applies normalization on the fly before the equality test. There are four available normalization forms: nfc, nfd, nfkc, and nfkd.

## References

* [Erlang Data Types](https://erlang.org/documentation/doc-15.0-rc1/doc/system/data_types.html)
* [Erlang Playground Testing out parsing code](https://www.mycompiler.io/view/A7Lq1y0D6nR)
* [Erlang calendar](https://www.erlang.org/doc/apps/stdlib/calendar.html#rfc3339_to_system_time/2)
* [Erlang Data Types](https://www.erlang.org/doc/system/data_types.html#number)
* [string](https://www.erlang.org/doc/apps/stdlib/string.html)
* [binary](https://www.erlang.org/doc/apps/stdlib/binary.html)
* [equal](https://www.erlang.org/doc/apps/stdlib/string.html#equal/4)