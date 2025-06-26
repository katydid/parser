# Decimal

`Decimal` is a numerical value with arbitrary precision, including decimals and large integers.

The `Decimal` strings returned by the Parser interface will be formatted in ISO 6093 format.

## ISO 6093

There is a preexisting standard for this: ISO 6093:1985 "Information processing — Representation of numerical values in character strings for information interchange."

> This International Standard specifies three presentations of fractional part. numerical values, which are represented in Character strings in a form readable by machine, for use in interchange between data processing Systems.

The ISO 6093 specifies three formats: NR1, NR2 and NR3.

Only the following characters are allowed:

```
a) digit = 0/1/2/3/4/5/6/7/8/9
b) sign = +/-
c) decimal-mark = , / .
d) space = SPACE
e) exponent-mark = E / e
```

NR1 is an integer without a decimal:

```
NR1 = unsigned-NR1 /signed-NR1
unsigned-NR1 = space* digit digit*
signed-NR1   = space* (sign/space) digit digit*
```

NR2 is an integer with a decimal, but without an exponent:

```
NR2 = unsigned-NR2/signed-NR2
unsigned-NR2 = (space* digit digit* decimal-mark digit*)
             / (space* digit* decimal-mark digit digit*)
signed-NR2   = (space* (sign/space) digit digit* decimal-mark digit*)
             / (space* (sign/space) digit* decimal-mark digit digit*)
```

NR3 is an integer with a decimal and an exponent:

```
NR3 = unsigned-NR3/signed-NR3
unsigned-NR3 = space* significand exponent-mark exponent
signed-NR3   = space* (sign/space) significand exponent-mark exponent
significand  = (digit digit* decimal-mark digit*)
             / (digit* decimal-mark digit digit*)
exponent     = sign? digit digit*
```

## References

* [ISO-6093-1985](https://cdn.standards.iteh.ai/samples/12285/039296509e8b40f3b25ba025de60365d/ISO-6093-1985.pdf)
* [Rust iso6093](https://docs.rs/iso6093/latest/iso6093/)