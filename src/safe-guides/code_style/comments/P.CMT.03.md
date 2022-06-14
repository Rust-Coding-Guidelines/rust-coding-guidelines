# P.CMT.03 Use line comments and avoid block comments

**[Description]**

Try to use line comments (`//` or `///`) rather than block comments. This is a convention in the Rust community.

For documentation comments, use `//! `, in other cases `///` is better.

Note: `#! [doc]` and `#[doc]` have a special role in simplifying document comments, and it is not necessary to force them into `//! ` or `//`.

**[Bad Case]**

```rust
// Bad

/*
 * Wait for the main task to return, and set the process error code
 * appropriately.
 */
mod tests {
    //! This module contains tests

    // ...
}
```

**[Good Case]**

When `normalize_comments = true`:

```rust
// Good

// Wait for the main task to return, and set the process error code
// appropriately.

// Good
// When defining modules using the `mod` keyword, 
// it is better to use `///` on top of `mod`.

/// This module contains tests
mod tests {
    // ...
}

// Good
#[doc = "Example item documentation"]
pub enum Foo {}
```

**【rustfmt configuration】**

| Parameter                                                                                    | Optional                         | Stable or not | Description                                                         |
| -------------------------------------------------------------------------------------------- | -------------------------------- | ------------- | ------------------------------------------------------------------- |
| [`normalize_comments`](https://rust-lang.github.io/rustfmt/?#normalize_comments)             | false(default) true(suggestionn) | No            | Convert the `/**/` comment to `/`                                   |
| [`normalize_doc_attributes`](https://rust-lang.github.io/rustfmt/?#normalize_doc_attributes) | false(default)                   | No            | Convert the `#! [doc]` and `#[doc]` annotations to `//! ` and `///` |