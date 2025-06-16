# Error

We decided to use a generic `Error` value in the description of the methods of the parser interface.
We also include `EOF`, not as an Error, but as a separate value in the description.

## Error value vs Exception vs Result type

This is an attempt at a language agnostic description of an error, exception, result type
and should be interpreted as what is most appropriate to the implementation language.

When we mention "returns a value or an error", this should be represented in the most efficient way specific to that programming language.

Examples of Error representations include:
* Exception
* Result
* Either
* Maybe
* Optional
* Sum Types/Tagged Unions
* Error value in a tuple

## Opaque

Also note that `Error` is opaque for a reason.
The user can make decisions on whether an error occured, but not what error occured as this level of transparency is not part of the interface.

## EOF

The `EOF` signal, is used to represent the end of the Parse.

If `EOF` is represented as an `Error`, as in for example `Golang`, then this is the only error that may be distinguished from other errors.

