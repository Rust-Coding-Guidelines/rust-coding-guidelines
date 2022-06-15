# P.FUD.01 Should rebind variables which pass into closure

**[Description]**

By default, closure captures environment variables with `borrow`, or it is also allowed to pass environment variables into closure with `move` keyword.

It is more readable to rebind and regroup these variables which pass into closure.

**[Bad Case]**

```rust
use std::rc::Rc;
let num1 = Rc::new(1);
let num2 = Rc::new(2);
let num3 = Rc::new(3);
let closure = {
    // ownership of `num1` has been moved
    let num2 = num2.clone();
    let num3 = num3.as_ref();
    move || {
        *num1 + *num2+ *num3; // Not Good.
    }
};
```


**[Good Case]**

```rust 
use std::rc::Rc;

let num1 = Rc::new(1);
let num2 = Rc::new(2);
let num3 = Rc::new(3);

// Good: rebind variables seperately, which would pass into closure.
let num2_cloned = num2.clone();
let num3_borrowed = num3.as_ref();
let closure = move || {
    *num1 + *num2_cloned + *num3_borrowed; // Good.
};
```



