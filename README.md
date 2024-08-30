# many-unzip

[![License](https://img.shields.io/crates/l/many-unzip.svg)](https://crates.io/crates/many-unzip)
[![Latest version](https://img.shields.io/crates/v/many-unzip.svg)](https://crates.io/crates/many-unzip)
[![Latest Docs](https://docs.rs/many-unzip/badge.svg)](https://docs.rs/many-unzip/)
[![downloads-badge](https://img.shields.io/crates/d/many-unzip.svg)](https://crates.io/crates/many-unzip)

[API docs](https://docs.rs/many-unzip/)

[`multiunzip` from itertools](https://docs.rs/itertools/latest/itertools/fn.multiunzip.html) but with support for larger than 12-tuples.

Converts an iterator of tuples into a tuple of containers.

`many_unzip()` consumes an entire iterator of k-tuples tuples, producing `k` collections, one for each column.
With default features, `many_unzip` supports up to 24-tuples.
Larger numbers can be enabled with feature flags, up to 192-tuples with the `192_tuple` feature.

This function is, in some sense, the opposite of [`multizip`](https://docs.rs/itertools/latest/itertools/fn.multizip.html).

```rust
# use many_unzip::many_unzip;

let inputs = vec![
    (1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13),
    (14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26),
    (27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39),
];

let (a, b, c, d, e, f, g, h, i, j, k, l, m): (
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
    Vec<_>,
) = many_unzip(inputs);

assert_eq!(a, vec![1, 14, 27]);
assert_eq!(b, vec![2, 15, 28]);
assert_eq!(c, vec![3, 16, 29]);
assert_eq!(d, vec![4, 17, 30]);
assert_eq!(e, vec![5, 18, 31]);
assert_eq!(f, vec![6, 19, 32]);
assert_eq!(g, vec![7, 20, 33]);
assert_eq!(h, vec![8, 21, 34]);
assert_eq!(i, vec![9, 22, 35]);
assert_eq!(j, vec![10, 23, 36]);
assert_eq!(k, vec![11, 24, 37]);
assert_eq!(l, vec![12, 25, 38]);
assert_eq!(m, vec![13, 26, 39]);
```
