# Rust

## Int64

> i64: The 64-bit signed integer type.

## Float64

> A 64-bit floating-point type (specifically, the “binary64” type defined in IEEE 754-2008).

## Decimal

rust-decimal:

> Decimal number implementation written in pure Rust suitable for financial and fixed-precision calculations.

astro-float: 

> Astro-float (astronomically large floating-point numbers) is an arbitrary precision floating-point numbers library designed for performance, portability, and implemented purely in Rust.

## Time

Rust supports RFC 3339

```
parse_from_rfc3339
```

It also supports parsing nanoseconds

```rust
extern crate chrono;

use chrono::*;

fn main() {
    let s = "2016-06-10T21:42:24.760738998Z";
    let dt = s.parse::<DateTime<UTC>>().unwrap();
    println!("{:?}", dt);

    // Prints 2016-06-10T21:42:24.760738998Z
}
```

And there is also a crate for RFC 9557: ixdtf

## Sum

```rust
enum IpAddr {
    V4(String),
    V6(String),
}
```

## References

* [Rust f64](https://doc.rust-lang.org/std/primitive.f64.html)
* [Rust i64](https://doc.rust-lang.org/std/primitive.i64.html)
* [ISO 8601 and Nanosecond Precision Across Languages](https://nickb.dev/blog/iso8601-and-nanosecond-precision-across-languages/)
* [Github chrono](https://github.com/chronotope/chrono/blob/bab97905ccfa5aa7ceae1ee131b41b7113ea4f6a/src/datetime/mod.rs#L676)
* [Crate ixdtf](https://docs.rs/ixdtf/latest/ixdtf/index.html)
* [astro-float](https://github.com/stencillogic/astro-float)
* [rust-decimal](https://github.com/paupino/rust-decimal)
* [Defining an Enum](https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html)