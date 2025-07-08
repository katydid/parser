# Float64

Every serialization format we [surveyed](./survey/Readme.md) supports double-precision floating-point format IEEE-754.

For this reason we support `Float64` as one of the `Kind`s and `Token` values.

```haskell
data Token =
  ...
  | Float64 Float64 -- '.' (IEEE-754)
  ...
```

We also found that all programming languages we [surveyed](./survey/language.md) supports IEEE-754 floats.
The one exception is Erlang, which supports IEEE-754, except for `NaN` and `Inf`.

## Comparing NaN

IEEE-754 specifies a double-precision floating point number.
One of the floating point numbers supported is `NaN` (not a number).
The specification also says that `NaN != NaN`.
This is important when calculating different `NaN`s, but this part of the spec is annoying when testing serializing and deserializing a `NaN`.
There is no way to test that the serialized `NaN` is equal to the deserialized `NaN`, without creating an exception to this rule.
For testing and validation purposes we recommend creating an exception to this rule where `NaN = NaN`.
When testing serialization and deserialization, please remember to not use default equality for `Float64`, rather use an equality that includes the exception and rather assumes that `NaN = NaN`.

## References

* [Milestones:IEEE Standard 754 for Binary Floating-Point Arithmetic, 1985 - Section: IEEE 754 in Programming Languages](https://ethw.org/Milestones:IEEE_Standard_754_for_Binary_Floating-Point_Arithmetic,_1985#IEEE_754_in_Programming_Languages)

