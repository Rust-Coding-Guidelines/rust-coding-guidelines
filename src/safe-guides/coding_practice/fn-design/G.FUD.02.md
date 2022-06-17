# G.FUD.02 Should input as reference if parameter derives `Copy` and its value inputed by-value is a big number

**[Level] Advice**

**[Description]**

By-value inputed parameters may emerge unnecessary `memcpy`, which could kill performance.

**[Bad Case]**

```rust
#![warn(clippy::large_types_passed_by_value)]

#[derive(Clone, Copy)]
struct TooLarge([u8; 2048]);

// Not Good
fn foo(v: TooLarge) {}
```

**[Good Case]**

```rust
#![warn(clippy::large_types_passed_by_value)]

#[derive(Clone, Copy)]
struct TooLarge([u8; 2048]);

// Good
fn foo(v: &TooLarge) {}
```

**[Lint Check]**

| lint name | Clippy check | Rustc check | Lint Group | Level |
| --------- | ------------ | ----------- | ---------- | ----- |
| [large_types_passed_by_value](https://rust-lang.github.io/rust-clippy/master/#large_types_passed_by_value) | yes | no | pedanic | allow |

This lint corresponds to the following configuration of `clippy.toml`

```toml
# if function is an exported api, then the lint would not be triggered, which aims to prevent devastated change for api. the default is true.
avoid-breaking-exported-api=true
```
