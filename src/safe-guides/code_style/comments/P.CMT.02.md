# P.CMT.02 Comments should have a width limit

**[Description]**

The width of each comment line should not be too long and needs to be set at a certain width, no more than 120, which help improve readability.

In `rustfmt`, the `comment_width` with `wrap_comments` configuration item can automatically split comments that exceed the width limit into multiple lines.

**Note**: The `use_small_heuristics` configuration item of `rustfmt` does not include `comment_width`.

**[Bad Case]**

```rust
// Bad
// Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
```

**[Good Case]**

When `comment_width=80` and `wrap_comments=true`.

**Note**: Here `wrap_comments` does not use the default value and needs to be configured to true.

```rust
// Good
// Lorem ipsum dolor sit amet, consectetur adipiscing elit,
// sed do eiusmod tempor incididunt ut labore et dolore
// magna aliqua. Ut enim ad minim veniam, quis nostrud
// exercitation ullamco laboris nisi ut aliquip ex ea
// commodo consequat.
```

**[rustfmt configuration]**

| Parameter                                                              | Optional                         | stable or not | Description                                                                              |
| ---------------------------------------------------------------------- | -------------------------------- | ------------- | ---------------------------------------------------------------------------------------- |
| [`comment_width`](https://rust-lang.github.io/rustfmt/?#comment_width) | 80(default)                      | No            | Specify the maximum width allowed for a line of comments                                 |
| [`wrap_comments`](https://rust-lang.github.io/rustfmt/?#wrap_comments) | false(default), true(suggestion) | No            | Running multi-line comments automatically change to multi-line comments by maximum width |