# P.NAM.01 The naming convention for identifiers in the same crate should use a uniform word order

**[Description]**

The particular choice of word order is not important, but pay attention to consistency within the crate and consistency with similar functionality in the standard library.

> For example:
>
> If the naming of types in crate were in **verb-object-error** word order, we need to follow the same order when we adding new types.

Here are some error types from the standard library:

- [`JoinPathsError`](https://doc.rust-lang.org/std/env/struct.JoinPathsError.html)
- [`ParseBoolError`](https://doc.rust-lang.org/std/str/struct.ParseBoolError.html)
- [`ParseCharError`](https://doc.rust-lang.org/std/char/struct.ParseCharError.html)
- [`ParseFloatError`](https://doc.rust-lang.org/std/num/struct.ParseFloatError.html)
- [`ParseIntError`](https://doc.rust-lang.org/std/num/struct.ParseIntError.html)
- [`RecvTimeoutError`](https://doc.rust-lang.org/std/sync/mpsc/enum.RecvTimeoutError.html)
- [`StripPrefixError`](https://doc.rust-lang.org/std/path/struct.StripPrefixError.html)

All of these use verb-object-error word order. If we were adding an error to represent an address failing to parse, for consistency we would want to name it in verb-object-error order like `ParseAddrError` rather than `AddrParseError`.

> Note: The `AddrParseError` of module `net` in the standard library is an exception. Most of the error types from the standard library follow the verb-object-error word order.

**[Bad Case]**

```rust
// Bad：Not the "verb-object-error" order, should be `ParseAddrError`
struct AddrParseError {}
```

**[Good Case]**

```rust
// Good: The order is the same as the standard library
struct ParseAddrError{}
```

