# Haskell

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

## References

* [Haskell Double](https://hackage.haskell.org/package/base-4.21.0.0/docs/Prelude.html#t:Double)
* [Haskell playground](https://play.haskell.org/saved/cJ9uFdnv)