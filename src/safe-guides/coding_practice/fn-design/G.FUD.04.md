# G.FUD.04 Should input by-value but by-ref if parameter derived `Copy`, and its value is a small enough number

**[Level] Advice**

**[Description]**

Generally, it is avoided to input by-ref when parameter's value is a small enough number and derived `Copy`. That's because as for such small values, from the perspective of performance, by-value is as fast as by-ref, and it could also make code more readable. It is also recommended to input by-value for some tiny `struct`, but should notice **[Exception]** cases.

**[Bad Case]**

```rust
#![warn(clippy::trivially_copy_pass_by_ref)]

// Not Good
fn foo(v: &u32) { ... }
```

**[Good Case]**

```rust
#![warn(clippy::trivially_copy_pass_by_ref)]

// Good
fn foo(v: u32) { ... }
```

**[Exception]**

Should notice following cases, lint checker would report trivial warnings because of its conservativeness.

```rust
#[derive(Clone, Copy)]
struct RawPoint {
    pub x: u8,
}

#[derive(Clone, Copy)]
struct Point {
    pub raw: RawPoint,
}

impl Point {
    pub fn raw(&self) -> *const RawPoint {
        &self.raw
    }

    // if you conform lint checker, change above `raw(&self)`'s parameter `&self` into `self`(delete ref), it is `raw_linted(self)`. That also works well in unoptimized cases(just like `cargo build`, the debug mode), but doesn't work in optimized cases(i.e. `cargo build --release`, the release mode) because of following reasons.
    pub fn raw_linted(self) -> *const RawPoint {
        &self.raw
    }
}

fn main() {
    let p = Point { raw: RawPoint { x: 10 } };

    // This passes
    assert_eq!(p.raw(), p.raw());

    // This fails
    // Actually, in optimized cases, the activity of function has been changed if not using `self` as shared ref.
    // Because struct Point derived Copy trait, everytime we call raw_linted() method, its instance would be copied, and return a different pointer.
    assert_eq!(p.raw_linted(), p.raw_linted());
}
```

**[Lint Check]**

| lint name | Clippy check | Rustc check | Lint Group | Level |
| --------- | ------------ | ----------- | ---------- | ----- |
| [trivially_copy_pass_by_ref](https://rust-lang.github.io/rust-clippy/master/#trivially_copy_pass_by_ref) | yes | no | pedanic | allow |

This lint corresponds to the following configuration of `clippy.toml`

```toml
# if it is an exported API, the lint checker would not be triggered, which avoid unexpected modifications.
avoid-breaking-exported-api=true

# consider the maximum size (bytes) of by-value pass with Copy. The default is None.
trivial-copy-size-limit=None
```
**Tips:** this lint would not consider the cases using pointer, just like example in **[Exception]** part. 

Reference of **[Exception]** example: [rust-clippy/issues/5953](https://github.com/rust-lang/rust-clippy/issues/5953).