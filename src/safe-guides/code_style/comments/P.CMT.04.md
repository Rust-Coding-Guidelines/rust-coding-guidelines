# P.CMT.04 File header comments include a copyright notice

**[Description]**

File header (i.e., module-level) comments should include the copyright notice first. If additional content needs to be added to the file header comments, it can be added under the copyright notice.

May include:

1. A description of the function of the document.
2. Author.
3. Creation date and last modification date.
4. Notes.
5. Open source license (e.g., Apache 2.0, BSD, LGPL, GPL).
6. Other.

The format of the copyright notice is as follows:

- 中文版：`版权所有（c）XXX 技术有限公司 2015-2022`。
- English version: `Copyright (c) XXX Technologies Co. Ltd. 2015-2022. All rights reserved. Licensed under Apache-2.0.`

Its content can be adjusted to participate in the following detailed description:

- `2015-2022` can be modified as needed. 2015 is the year the file was first created and 2022 is the year the file was last modified. It is possible to write only one creation year, so that the copyright notice does not need to be changed if the file is modified frequently.
- For internal use, there is no need to add `All rights reserved`.
- `Licensed under Apache-2.0.`, if it is open source then you can add the license statement.

Caution when writing copyright notes:

- Copyright notes should be written from the top of the file header.
- The header comment should contain the "copyright notice" first, followed by the rest of the content.
- Optional content should be added as needed to avoid empty formatting without content.
- Maintain uniform formatting, either by the project or by the larger context.
- Maintain a neat layout, with line breaks aligned.

**[Good Case]**

```rust
// Good
// 版权所有（c）XXX 技术有限公司 2015-2022。

// Or

// Good
// Copyright (c) XXX Technologies Co.Ltd. 2015-2022. 
// All rights reserved. Licensed under Apache-2.0.
```