# Design

This document describes how design decisions were made.

In validation languages that are optimized properly the parser becomes the bottleneck.
This is one reason performance is important and why we recommend:

* The parser only ever moves forward and does not do any backtracking.
* The parser should avoid copying or allocating memory on the heap as much as possible.
* The parser should only parse what truly needs parsing and skip as much as possible.

We found that [most serialization formats are Sequential](./survey/comparison.md) and have decided on an interface with three methods:

* Next
* Skip
* Token

Deciding which types to represent took us on a journey of doing a [survey](./survey/Readme.md) of the most common serialization formats,
we have come with a limited set of supported [Scalar](./scalar.md) and [Compound](./compound.md) types.

Other types can be mapped from rarer types to these supported types. 
For example, UUID is mapped to `Bytes`, Dates to `String` via ISO 8601, Set to `List` and an Object is repesented as a `Map`.
