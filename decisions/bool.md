# Bool

The bool values are represented as part of the `Kind` or `Token` type:

```haskell
data Token =
  ...
  | False -- 'f'
  | True -- 't'
  ...
```

This is to minimize the interface for programming languages that do not support sum types.

In a language without sum types, we need to the multiple methods to tokenize the value:

```
Tokenize : () -> (Kind | error)
Int64: () -> (int64 | error)
Float64: () -> (float64 | error)
Bytes: () -> ([]byte | error)
```

If `Kind` did not include 'f' and 't', then the interface would need another method:

```
Tokenize : () -> (Kind | error)
Int64: () -> (int64 | error)
...
Bool: () -> (bool | error)
```

We want to keep the interface small and it only adds one extra `Kind`, which is better than adding another method.

