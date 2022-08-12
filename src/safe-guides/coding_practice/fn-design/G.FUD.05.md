# G.FUD.05 Don't always specify `#[inline(always)]` for function

**[Level] Advice**

**[Description]**

`inline` could imporve performance, but also increase compilation time and size. You have to make a tradeoff among Performance, Compilation time and Compilation size in Rust, and it is recommended to use `inline` on demand.


**[Bad Case]**

```rust
#![warn(clippy::inline_always)]

// Not Good
#[inline(always)]
fn not_quite_hot_code(..) { ... }
```

**[Exception]**

Use `inline` on demand. i.e. it is obvious that one function is called frequently, and you could use `inline` for it to improve performance.

```rust
// Good: that function is often called for recycle buffer memory, so use `inline` maximize its performance.
pub fn buf_recycle(buf_id: usize) {
    // ...
}
```

**[Lint Check]**

| lint name | Clippy check | Rustc check | Lint Group | Level |
| --------- | ------------ | ----------- | ---------- | ----- |
| [inline_always](https://rust-lang.github.io/rust-clippy/master/#inline_always) | yes | no | pedanic | allow |

