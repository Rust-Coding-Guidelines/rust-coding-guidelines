# P.CMT.01 The code can be self-annotated, and the documentation should be concise

**[Description]**

一、The code can be self-annotated, avoiding redundant ordinary code comments.

Comments are important, but the best code is documentation itself. Meaningful type, function, and variable names are far better than ambiguous names explained by comments. Comments are used when meaningful type names, function names, and variable names cannot express complete semantics.

Don't describe obvious phenomena, and never translate code in natural language as comments.

二、The documentation should be concise.

1. The content and terms in the documentation comments should be as short and concise as possible, and should not be too long. Make sure your code is well commented and understandable by others. Good comments convey the context and purpose of the code.
2. Comments are always structured around two key points:
   - What: Used to describe what the code implement.
   - How: Used to describe how to use code your code.
3. The natural language used for comments and documentation comments should be consistent.
4. Rust project documentation should always be built on the `rustdoc` tool. `rustdoc` supports the Markdown format. To make the documentation more beautiful and readable, the documentation comments should use the Markdown format.

**[Good Case]**

Module Based Documentation Comments. From Rust std `std::vec`:

```rust
// Good

//! # The Rust core allocation and collections library
//!
//! This library provides smart pointers and collections for managing
//! heap-allocated values.
//!
//! This library, like libcore, normally doesn’t need to be used directly
//! since its contents are re-exported in the [`std` crate](../std/index.html).
//! Crates that use the `#![no_std]` attribute however will typically
//! not depend on `std`, so they’d use this crate instead.
//!
//! ## Boxed values
//!
//! The [`Box`] type is a smart pointer type. There can only be one owner of a
//! [`Box`], and the owner can decide to mutate the contents, which live on the
//! heap.
```

General Documentation Comments. From Rust std `Vec::new` method.

```rust
// Good

/// Constructs a new, empty `Vec<T>`.
///
/// The vector will not allocate until elements are pushed onto it.
///
/// # Examples
///
/// ```
/// # #![allow(unused_mut)]
/// let mut vec: Vec<i32> = Vec::new();
/// ```
#[inline]
#[rustc_const_stable(feature = "const_vec_new", since = "1.39.0")]
#[stable(feature = "rust1", since = "1.0.0")]
pub const fn new() -> Self {
    Vec { buf: RawVec::NEW, len: 0 }
}
```