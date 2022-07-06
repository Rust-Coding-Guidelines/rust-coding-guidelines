# G.FUD.03 Should refactor into customized `struct` or `enum` if there are too many `bool` type's function parameters

**[Level] Advice**

**[Description]**

Too many `bool` parameters is bad for memory and prone to issue errors. As to use typeinference and borrowchecker effectively, we should refactor into cutomized `struct` and `enum` in this case.

**[Bad Case]**

```rust
#![warn(clippy::fn_params_excessive_bools)]

// Not Good
fn f(is_rould: bool, is_hot: bool) { ... }
```

**[Good Case]**

```rust
#![warn(clippy::fn_params_excessive_bools)]

enum Shap {
    Round,
    Spiky,
}

enum Temperature {
    Hot,
    IceCold,
}

// Good
fn f(shape: Shape, temperature: Temperature) { ... }
```

**[Lint Check]**

| lint name | Clippy check | Rustc check | Lint Group | Level |
| --------- | ------------ | ----------- | ---------- | ----- |
| [fn_params_excessive_bools](https://rust-lang.github.io/rust-clippy/master/#fn_params_excessive_bools) | yes | no | pedanic | allow |

This lint corresponds to the following configuration of `clippy.toml`

```toml
# In order to limit maximum number of bool type's parameters, the default is 3.
max-fn-params-bools=3
```
