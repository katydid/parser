# Haskell

## Int64

> Int is Bounded, which means that you can use minBound and maxBound to find out the limits, which are implementation-dependent but guaranteed to hold at least [-2^29 .. 22^9-1].

```
Prelude> (minBound, maxBound) :: (Int, Int)
(-9223372036854775808,9223372036854775807)
```

This means on certain platforms Haskell supports the full int64 number.

## Float64

Numeric.Floating.IEEE:

> This module provides IEEE 754-compliant operations for floating-point numbers.

## Decimal

Stack Overflow:

> If you want numbers that are (arbitrarily) more accurate than Double or Float, use Scientific offered by the scientific package. 

Scientific:

> do note that since we're using an Int to represent the exponent these numbers aren't truly arbitrary precision. I intend to change this to Integer in the future!

## Time

Haskell supports RFC3339 with nanoseconds

```haskell
import Data.Time
import Data.Time.Format (defaultTimeLocale, parseTimeM)

-- Parses RFC 3339 timestamp with nanosecond precision
parseRFC3339 :: String -> Maybe UTCTime
parseRFC3339 = parseTimeM True defaultTimeLocale "%Y-%m-%dT%H:%M:%S%Q%Z"

main :: IO ()
main = do
    let timestamp = "2025-06-25T14:45:00.123456789+01:00"
    case parseRFC3339 timestamp of
        Just t  -> putStrLn $ "Parsed time: " ++ show t
        Nothing -> putStrLn "Failed to parse timestamp"
```

```
$ Parsed time: 2025-06-25 13:45:00.123456789 UTC
```

## Char

> The character type Char represents Unicode codespace and its elements are code points as in definitions D9 and D10 of the Unicode Standard.

## References

* [Haskell Double](https://hackage.haskell.org/package/base-4.21.0.0/docs/Prelude.html#t:Double)
* [Haskell playground](https://play.haskell.org/saved/cJ9uFdnv)
* [Stack Overflow: What is the difference between Int and Integer?](https://stackoverflow.com/questions/3429291/what-is-the-difference-between-int-and-integer)
* [Numeric.Floating.IEEE](https://hackage.haskell.org/package/fp-ieee-0.1.0.5/docs/Numeric-Floating-IEEE.html)
* [Stack Overflow: Set precision in Haskell](https://stackoverflow.com/questions/28516337/set-precision-in-haskell)
* [Data.Scientific](https://github.com/basvandijk/scientific)
* [Data.Char](https://hackage.haskell.org/package/base-4.21.0.0/docs/Data-Char.html)