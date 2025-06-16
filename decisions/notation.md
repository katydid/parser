# Notation

In this document, we explain notation decisions and explain the notation.

The Katydid Parser is a generic interface created to be implemented for many serialization formats in a variety of programming languages.
This requires a language agnostic notation.

## Functions

We choose to describe the function signatures as method signatures, so that it is understandable to imperative programmers.
Functional programmers will find it easier to compensate for the inprecise description.

The parser interface has the following interface:

* `Next (): (Hint | Error | EOF)`
* `Skip (): (Error | EOF)?`
* `Token (): ((Kind, Value) | Error)`

The `()` indicates that none of the methods take any parameters.

The return type follows the `:` character.

The return paramter is in parenthesis `()` with composition either using a `|`, `,` and/or `?`:
* The `|` represents disjunction (or), which means that `Next` method returns a `Hint` or an `Error` or an `EOF` signal.
* The `?` represents an `Optional`, which means that the `Skip` method returns an `Error` or an `EOF` signal or `None` (null).
* The `,` represents a `Tuple`, which means that the `Token` method returns a (`Kind` and `Value`) or an `Error`.

## Implementation in a Functional language

These signatures are not pure functions, but rather methods.
This means that these methods are also modifying an internal state.

Turning these methods into pure functions requires adding a state input parameter and state output result:
```
Next (state): (state, (Hint | Error | EOF))`
```

This is a perfect use case for a State Monad:
```
Next (): State (Hint | Error | EOF)`
```
