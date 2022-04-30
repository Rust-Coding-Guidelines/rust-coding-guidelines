# G.CMT.02 If a Panic occurs under certain circumstances in the public API, add a Panic comment to the corresponding document

**[Level]** Requirements

**[Description]**

In the public (pub) function documentation, it is recommended to add `# Panic` comments to explain under what conditions the function will Panic, so that users can pre-process it.

Description: This rule is detected by cargo clippy. It does not warn by default.

**[Bad Case]**

```rust
#![warn(clippy::missing_panics_doc)]

// Bad：If do not add Panic relevant comments.`Clippy` will raise error: "warning: docs for function which may panic missing `# Panics` section"。
pub fn divide_by(x: i32, y: i32) -> i32 {
    if y == 0 {
        panic!("Cannot divide by 0")
    } else {
        x / y
    }
}
```

**[Good Case]**

```rust
#![warn(clippy::missing_panics_doc)]

// Good：Added Panic comments
/// # Panics
///
/// Will panic if y is 0
pub fn divide_by(x: i32, y: i32) -> i32 {
    if y == 0 {
        panic!("Cannot divide by 0")
    } else {
        x / y
    }
}
```

**[Lint detect]**

| Lint name                                                                                            | Clippy detectable | Rustc detectable | Lint Group | Default level |
| ---------------------------------------------------------------------------------------------------- | ----------------- | ---------------- | ---------- | ------------- |
| [missing_panics_doc ](https://rust-lang.github.io/rust-clippy/master/index.html#missing_panics_doc ) | yes               | no               | Style      | allow         |

Default is `allow`，But this pricipal need to be set `#![warn(clippy::missing_panics_doc)]`。