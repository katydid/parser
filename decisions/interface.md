# Interface

The parser interface has 3 methods:

* `Next : () -> (Hint | Error | EOF)`
* `Skip : () -> (Error | EOF)?`
* `Token : () -> ((Kind, value) | Error)`

This documentation is an explanation of the top level interface decisions.
The design of the rest of interface is explained in:
* [Hint](./hint.md)
* [Kind](./kind.md)
* [Error](./error.md)

## Optimized

In validation languages that are optimized properly the parser becomes the bottleneck.
This is one reason performance is important and why we recommend:

* The parser only ever moves forward and does not do any backtracking.
* The parser should avoid copying or allocating memory on the heap as much as possible.
* The parser should only parse what truly needs parsing and skip as much as possible.

## Sequential

The interface does sequential parsing, since the interface is optimized for parsing serialization formats.
We did a [survey](./survey/Readme.md) of serialization formats and found that [most serialization formats are Sequential](./survey/comparison.md).

This interface also has room for a non sequential, but forward moving method: `JumpTo (key): (Error|EOF)`, which could be added in future,
to make sure we take advantage of some pointer based serialization format's optimizations.

## Minimal

We believe a minimal interface is a better interface.
This is the smallest interface that doesn't compromise speed that we could come up with:

* `Next` parses over to the next token, but does not tokenize it if not necessary.
* `Skip` is aware that this is a parse tree and skips the parsing of whole branches.
* `Token` makes sure we only tokenize, which can allocate memory, when absolutely necessary (when the user asks).


