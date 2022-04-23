## P.NAM.05 The `getter` family of methods used to access or retrieve data should not normally have the prefix `get_`

**[Description]**

Because of Rust's ownership semantics, both methods' parameters in following cases use shared reference `&self` or exclusive reference `&mut self` , which represent `getter` semantics.

> `getter` semantics always mean to return an object but a reference in Rust's ownership conventions.

There are also some exceptions to use `get_` prefix.


**[Bad Case]**
```rust
pub struct First;
pub struct Second;

pub struct S {
    first: First,
    second: Second,
}

impl S {
    // Bad: Shouldn't use 'get_' prefix to name accesssing member function.
    pub fn get_first(&self) -> &First {
        &self.first
    }

    // Bad：
    // `get_mut_first`, or `mut_first` are also not good.
    pub fn get_first_mut(&mut self) -> &mut First {
        &mut self.first
    }

    // set_ prefix is fine.
    pub fn set_first(&mut self, f: First) -> &mut First {
        self.first = f;
    }
}
```


**[Good Case]**

```rust
pub struct First;
pub struct Second;

pub struct S {
    first: First,
    second: Second,
}

impl S {
    // Ok
    pub fn first(&self) -> &First {
        &self.first
    }

    // Ok
    pub fn first_mut(&mut self) -> &mut First {
        &mut self.first
    }

    // set_ prefix is fine.
    pub fn set_first(&mut self, f: First) -> &mut First {
        self.first = f;
    }
}
```

**[Exception]**

However, there are also some exceptions: Only in cases to retrieve data by `getter` explicitly, could name with `get_` prefix. For example, `Cell::get` could access the data in one `Cell`.

For `getter` checked in runtime, such as bounds checking, we could consider to add an Unsafe `_unchecked` methods. Generally, there would be following function signatures.

```rust
// Do some checks in runtime, such as bounds checking.
fn get(&self, index: K) -> Option<&V>;
fn get_mut(&mut self, index: K) -> Option<&mut V>;
// No runtime checking, use to improve performance in some case. 
// For examplem, when executed in an execution environment,which is impossible to trigger bounds checking.
unsafe fn get_unchecked(&self, index: K) -> &V;
unsafe fn get_unchecked_mut(&mut self, index: K) -> &mut V;
```
There is almost no such distinction between `getter` and type conversion ([G.NAM.02](./G.NAM.02.md)). For instance, [`TemDir::path`](https://docs.rs/tempdir/0.3.7/tempdir/struct.TempDir.html#method.path) could be regarded as a `getter`, which represents the filesystem's path of temporary directory, and [`TemDir::into_path`](https://docs.rs/tempdir/0.3.7/tempdir/struct.TempDir.html#method.into_path) is in charge of sending converted data when deleting temporary directory
to callee.

There would not result for redundancy with naming the method as `path`, because `path` itself is a `getter`, otherwise if you name it as `get_path` or `as_path`.

[`TempDir::path`]: https://docs.rs/tempdir/0.3.7/tempdir/struct.TempDir.html#method.path
[`TempDir::into_path`]: https://docs.rs/tempdir/0.3.7/tempdir/struct.TempDir.html#method.into_path

Implementations in `StandardLibrary`:

- [`std::io::Cursor::get_mut`](https://doc.rust-lang.org/std/io/struct.Cursor.html#method.get_mut)
- [`std::ptr::Unique::get_mut`](https://doc.rust-lang.org/std/ptr/struct.Unique.html#method.get_mut)
- [`std::sync::PoisonError::get_mut`](https://doc.rust-lang.org/std/sync/struct.PoisonError.html#method.get_mut)
- [`std::sync::atomic::AtomicBool::get_mut`](https://doc.rust-lang.org/std/sync/atomic/struct.AtomicBool.html#method.get_mut)
- [`std::collections::hash_map::OccupiedEntry::get_mut`](https://doc.rust-lang.org/std/collections/hash_map/struct.OccupiedEntry.html#method.get_mut)
- [`<[T]>::get_unchecked`](https://doc.rust-lang.org/std/primitive.slice.html#method.get_unchecked)
