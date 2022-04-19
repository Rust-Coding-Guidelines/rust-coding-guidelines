# 2.2 Format

A uniform coding style is developed to improve the readability of code and make it easier to maintain daily code and review code between teams.

Rust has an automated formatting tool, rustfmt, to help developers get rid of the manual work of formatting code and improve productivity. However, what style specification rustfmt follows, as developers need to understand, when writing code can be proactively written in such a style.

**Description**:

For unstable configuration items in `rustfmt` (`Stable` is `No`), it means that the configuration item cannot be changed in the stable (Stable) version of Rust, but its default value will take effect when `cargo fmt`. Under Nightly Rust, all configurations can be customized.

For information on how to use unstable configuration items in Stable Rust, sample configurations, and other global configuration item descriptions, see: [Rustfmt Configuration Description](./../Appendix/tools/rustfmt.md).

**Caution**

Because the rustfmt tool automatically modifies code, to ensure that rustfmt does not accidentally change the wrong code, you should pay attention to the following two descriptions when using rustfmt: 1.

1. Always make sure that the rustfmt command is executed after all the code has been modified and compiled. Because the code is not compiled during rustfmt execution, there is no static check protection. 2.

2. If you are using an IDE or editor with automatic protection turned on, do not turn on automatic rustfmt execution.
