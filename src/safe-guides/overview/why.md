# 1.1 Why you need the Rust coding specification ?

When I first learned Rust, I marveled at the sophistication of the tools Rust provides. For example, rustfmt, which automatically formats code, and clippy, which helps you standardize code that is not written properly. They are truly excellent tools. At the time, I didn't think Rust needed to be coded at all like other languages.

But as I learned more and more about Rust, I came to realize that these tools had a lot of shortcomings and did not cover everything. For example, improper configuration and use of rustfmt can lead to code errors and inability to recognize the semantics of various naming in Rust code; clippy has some false positives or lint is not reasonable, and can not cover to Unsafe Rust and other issues. Developers, especially newcomers, if they rely on rutfmt and clippy for a long time like using a black box, but do not understand the reason behind their lint, just know the reason but not the reason, it is impossible to improve the development efficiency under the premise that the code quality has certain requirements.

So, rutfmt and clippy are not a panacea. We also need a comprehensive and universal coding specification that also covers tools like rustfmt and clippy, so that the majority of Rust teams can quickly implement Rust and enhance collaboration and trust between teams by standardizing the principles and rules to understand the basic framework for writing authentic Rust code.

## Limitations of Rustfmt and Clippy

### Limitations of Rustfmt

Rust has an automatic formatting tool, rustfmt, which helps developers get rid of the manual work of formatting code and increase productivity. However, it does not replace the coding specification to standardize the coding style of Rust code.

The main drawbacks of rustfmt are the following.

1. The naming of variables, types, functions, etc. in Rust contains semantics, especially ownership semantics. rustfmt tool cannot determine the naming semantics in the code. This aspect can be partially satisfied by using Clippy, but it is rather one-sided for developers.
2. rustfmt can cause problems if used improperly or configured improperly. Because rustfmt is an auto-formatting tool, it automatically modifies the code, but it does not compile when it modifies the code. If the developer configures autosave and then executes rustfmt automatically, it will cause the code to be modified incorrectly. Or, there are some configuration options for rustfmt that are misconfigured, which will also cause the code to be modified incorrectly.
3. The configuration items of rustfmt tool are fragmented, and most developers do not understand the meaning of each configuration item.
4. rustfmt does not have a coding specification that covers code comments and documentation comments.

In summary, there is a need to provide a common coding specification so that developers clearly understand what coding style Rust follows overall in terms of naming, formatting and commenting. It will cover the content of rustfmt, but not mechanically extract the rules of rustfmt one by one, but a unified categorization and organization of the rules of rustfmt, to facilitate developers to understand the rules set in rustfmt, and to facilitate the team to form their own code style.

### Clippy's limitations

Clippy is a linter for Rust, one of the main components of the Rust ecosystem. It performs additional static checks on developed code, reports problems found and explains how to fix them (sometimes it can even fix them automatically). Using it can be beneficial for Rust beginners and even professionals.

However, using Clippy does not mean that it can replace coding specifications, and it has many drawbacks: 

1. Unsafe Rust is a very important part of Rust and needs to be covered by a complete coding specification to help developers write safe Unsafe code.
2. there are more than 500 lint in Clippy so far, and there is a growing trend. it is impossible for developers to understand each lint one by one, so a coding specification is needed to help developers to sort out and categorize lint.
3. there is some controversy about the suggestion and classification (allow/warning/deny) of lint in Clippy. Some lint is allow by default, but it does not mean that it is reasonable to write in some scenarios; similarly, some lint is warning, but it does not mean that it is unreasonable in some scenarios. For this reason, dtolnay also created this repository: [https://github.com/dtolnay/noisy-clippy](https://github.com/dtolnay/noisy-clippy) for analyzing how many Clippy lint's in the community crate suggestions does not match the actual scenario, so as to achieve the goal of improving Clippy.

In summary, Clippy is a very useful tool, but it is not a replacement for coding specifications.