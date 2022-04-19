# Overview

[《Rust 编码规范》 中文版](https://rust-coding-guidelines.github.io/rust-coding-guidelines-zh/)

> WIP.See the Chinese version for the full version, the English version is currently being translated from the Chinese version, welcome to participate in the contribution!

## Lists

- [1.1 Why you need the Rust coding specification ?](./overview/why.md)
- [1.2 Basic conventions of the coding specification](./overview/convention.md)

## Introduce

It is understood that some companies and organizations within the Rust community maintain their own coding specifications. Some of the publicly available ones are listed below.


- [Rust API Guidelines](https://rust-lang.github.io/api-guidelines/about.html)
- [Rust Style Guide](https://github.com/rust-dev-tools/fmt-rfcs/blob/master/guide/guide.md)
- [Rust's Unsafe Code Guidelines Reference](https://rust-lang.github.io/unsafe-code-guidelines/)
- [ANSSI | Secure Rust Guidelines](https://anssi-fr.github.io/rust-guide)
- [PingCAP | Rust Style Guide](https://github.com/pingcap/style-guide)
- [Google Fuchsia  OS Rust Guide](https://fuchsia.dev/fuchsia-src/development/languages/rust)
- [RustAnalyzer Style Guide](https://github.com/rust-analyzer/rust-analyzer/blob/master/docs/dev/style.md)
- [Clippy lints](https://rust-lang.github.io/rust-clippy/master/index.html)
- [lints in the rustc book ](https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html)
- [Noisy Clippy](https://github.com/dtolnay/noisy-clippy)
- [Rustfmt Rules](https://rust-lang.github.io/rustfmt/?version=v1.4.38&search=)

## The role of coding specifications

1. Improve the readability, maintainability, robustness, and portability of code by following Rust language features. 
2. Improve the standardization and security of Unsafe Rust code writing. 
3. The programming specification terms strive to systematize, easy to apply, easy to check, to help developers improve development efficiency.
4. give developers a clear and global vision, in the process of developing code can follow a good code specification, rather than wait until the code is written and then through rustfmt and clippy such tools, a line to modify the warning.
5. The specification is not a tutorial, but the level of developers varies. For some knowledge blind spots and those that may lead to program errors, the specification will also cover.
