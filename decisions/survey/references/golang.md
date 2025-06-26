# Golang

## Int64

> int64 is the set of all signed 64-bit integers. Range: -9223372036854775808 through 9223372036854775807.

## Float64

> float64 is the set of all IEEE 754 64-bit floating-point numbers.

## Decimal

> Package big implements arbitrary-precision arithmetic (big numbers). The following numeric types are supported: ... Float ...

The Float.Parse method seems to support arbitrary precision decimals.

## Time

Parses RFC 3339 via `time.RFC3339` and Nanoseconds via `time.RFC3339Nano`

## References

* [int64](https://pkg.go.dev/builtin#int64)
* [float64](https://pkg.go.dev/builtin#float64)
* [time package](https://pkg.go.dev/time)
* [math/big](https://pkg.go.dev/math/big#Float.Parse)