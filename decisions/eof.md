# EOF

The `EOF` signal, is used to represent the end of the Parse.

It is represented as different from an `Error`, to make it clear that this needs to be checked and will be signaled in a checkable way.

For example, in `Golang`, we represent this inside the `error` type, but it is checkable via: `err == io.EOF`.
Other languages might prefered a separate `EOF` value in sum type of their own.