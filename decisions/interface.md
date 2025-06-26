# Interface

The parser interface has 3 methods:

* `Next : () -> (Hint | Error | EOF)`
* `Skip : () -> (Error | EOF)?`
* `Token : () -> ((Kind, value) | Error)`

This document is an explanation of the top level interface decisions.
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

## Pull-based

The parser is a pull-based parser.
This means it only pulls the next token, once the user asks for it.

We do not want to parse the whole tree, since this would require allocating memory, which would not be as performant.

Another solution to this would be to use a event-based parser.
An event-based parser would use callback to ensure not having to keep the whole parse tree in memory at one time.
It is also quite performant, since the event-based parser, allows the user to skip parsing parts of the parse tree.
The user can do this by returning some parsing signal from the callback.

A pull-based parser offers just a slightly higher level of control.
For example, in an event-based parser, the parser would parse the token to the user, but the user might not have wanted that token to be tokenized.

## Sequential

The interface does sequential parsing, since the interface is optimized for parsing serialization formats.
We did a [survey](./survey/Readme.md) of serialization formats and found that [most serialization formats are Sequential](./survey/comparison.md).

This interface also has room for a non sequential, but forward moving method: `JumpTo (field): (Error|EOF)`, which could be added in future,
to make sure we take advantage of some pointer based serialization format's optimizations.

## Minimal

We believe a minimal interface is a better interface.
This is the smallest interface that doesn't compromise speed that we could come up with:

* `Next` parses over to the next token, but does not tokenize it if not necessary.
* `Skip` is aware that this is a parse tree and skips the parsing of whole branches.
* `Token` makes sure we only tokenize, which can allocate memory, when absolutely necessary (when the user asks).
