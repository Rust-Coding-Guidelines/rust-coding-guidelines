# G.FUD.01 Less than 5 function parameters

**[Level] Advice**

**[Description]**

In order to improve readability of code, it's better to set less than 5 function's parameters.


**[Bad Case]**

```rust
struct Color;
// Not Good
fn foo(x: f32, y: f32, name: &str, c: Color, w: u32, h: u32, a: u32, b: u32) {
    // ..
}
```

**[Good Case]**

Refine function's parameters as possible.

```rust
struct Color;
// Good: use const generic here to receive multiple u32 typed parameters afterward.
// use tuple to refine 2~3 parameters as one.
fn foo<T, const N: usize>(x: (f32, f32), name: &str, c: Color, last: [T;N]) {
    ;
}

fn main() {
    let arr = [1u32, 2u32];
    foo((1.0f32, 2.0f32), "hello", Color, arr);
    let arr = [1.0f32, 2.0f32, 3.0f32];
    foo((1.0f32, 2.0f32), "hello", Color, arr);
}
```

**[Lint Check]**

| lint name | Clippy check | Rustc Check | Lint Group | level |
| --------- | ------------ | ----------- | ---------- | ----- |
| [too_many_arguments](https://rust-lang.github.io/rust-clippy/master/#too_many_arguments) | yes | no | complexity | warn |

This lint corresponds to the following configuration of `clippy.toml`:

```toml
# less than 5 parameters
too-many-arguments-threshold=5
```
