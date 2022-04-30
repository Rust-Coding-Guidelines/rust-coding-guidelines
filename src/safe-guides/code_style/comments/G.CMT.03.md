# G.CMT.03 Use spaces in document comments instead of tabs

**[Level]** Suggestion

**[Description]**

Rust code style promotes the use of **four spaces** instead of tabs, and **four spaces** should be used consistently in the documentation comments.

**[Bad Case]**

Tab is used in the following document comments.

```rust
// Bad：Tab indentation is used in document comments
///
/// Struct to hold two strings:
/// 	- first		one
/// 	- second	one
pub struct DoubleString {
   ///
   /// 	- First String:
   /// 		- needs to be inside here
   first_string: String,
   ///
   /// 	- Second String:
   /// 		- needs to be inside here
   second_string: String,
}
```

**[Good Case]**

```rust
// Good：Four spaces indentation is used in document comments
///
/// Struct to hold two strings:
///     - first        one
///     - second    one
pub struct DoubleString {
   ///
   ///     - First String:
   ///         - needs to be inside here
   first_string: String,
   ///
   ///     - Second String:
   ///         - needs to be inside here
   second_string: String,
}
```

**[Lint detect]**

| Lint name                                                                                                | Clippy detectable | Rustc detectable | Lint Group | Default level |
| -------------------------------------------------------------------------------------------------------- | ----------------- | ---------------- | ---------- | ------------- |
| [tabs_in_doc_comments ](https://rust-lang.github.io/rust-clippy/master/index.html#tabs_in_doc_comments ) | yes               | no               | Style      | warn          |
s