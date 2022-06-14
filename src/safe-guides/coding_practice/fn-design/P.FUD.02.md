# P.FUD.02 Don't Use `return` for return value

**[Description]**
In such that function would automatically return the value of last expression in Rust, it is not required to use `return` explicitly.

Only when it is necessary to return a value in procedure of function, should use `return` explicitly.

**[Bad Case]**
```rust
fn foo(x: usize) -> usize {
    if x < 42 {
        return x;
    }
    return x + 1; // Not Good
}
```
**[Good Case]**
```rust
fn foo(x: usize) -> usize {
    if x < 42 {
        return x;
    }
    x + 1 // Good
}
```


