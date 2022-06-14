# G.CMT.01 Error comments need to added the documentation of functions that return `Result` types in the public

**[Level]** Suggestion

**[Description]**

In the public (pub) documentation of functions that return `Result` types, it is recommended to add `# Error` comments to explain what scenarios the function will return what kind of error type, so that users can easily handle errors.

Description: This rule can be detected by cargo clippy, but it does not warn by default.

**[Bad Case]**

```rust
#![warn(clippy::missing_errors_doc)]

use std::io;
// Bad： Clippy will be warned "warning: docs for function returning `Result` missing `# Errors` section"
pub fn read(filename: String) -> io::Result<String> {
    unimplemented!();
}
```

**[Good Case]**

```rust
#![warn(clippy::missing_errors_doc)]

use std::io;
// Good：adding normatives Errors documentation comments

/// # Errors
///
/// Will return `Err` if `filename` does not exist or the user does not have
/// permission to read it.
pub fn read(filename: String) -> io::Result<String> {
    unimplemented!();
}
```

**[Lint detection]**

| Lint name                                                                                            | Clippy detectable | Rustc detectable | Lint Group | Default level |
| ---------------------------------------------------------------------------------------------------- | ----------------- | ---------------- | ---------- | ------------- |
| [missing_errors_doc ](https://rust-lang.github.io/rust-clippy/master/index.html#missing_errors_doc ) | yes               | no               | Style      | allow         |