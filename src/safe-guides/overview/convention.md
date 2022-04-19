# 1.2 Basic conventions of the coding specification

**Programming specifications are in no way written to increase the burden on developers and are intended to help developers write high-quality Rust code.**

To accomplish this, the specification terms are divided into two categories: **Principles** and **Rules**.

- A principle is a general direction that guides programming development, or refers to a class of situations. There are also a few principles that are detectable by the Rust compiler, but because the compiler diagnostic information is confusing, principles are added to help developers avoid such situations.

- Rules, as opposed to principles, are more specific and contain positive and negative examples to further illustrate them. Some rules also add exceptions. The rules are basically detectable by lint.

## Rule content Relationship with rustfmt and clippy

The specification is divided into two main parts: code style and code practice.

**Code style**

Code naming, formatting and comments are included in the code style.

- The naming part, mainly by clippy lint to check, some naming rules clippy lint does not provide detection, then need to custom lint to support.
- The format part, mainly using rustfmt to automatically modify, the rules in the coding specification describes most of the configuration items of rustfmt by category, in order to facilitate developers to make reference and develop their own configuration items. Configuration templates are also provided in the coding specification.
- The comments section, which includes general comments and documentation comments, rule entries are regulated through a collaboration between rustfmt and clippy.

**Code Practices**

The code practices are categorized by Rust language features, and each language feature is summarized as much as possible for everyday coding best practices, extracted into a list of principles and rules for developers to refer to. Most of the rules are recommendations, and the rules that are required are basically security-related.

Clippy lint involves a lot of skillful lint, so it is not put into the specification.

The **rules mainly focus on generic scenarios, code readability, maintainability, security, performance of the four considerations, it only covers a small part (less than 1/5) clippy lint**. There are also rules that are not available in the clippy lint and require custom lint.

The focus of the code practice content is on the Unsafe Rust coding specification, which has more coding principles than rules, and which is rarely detected by Clippy lint. There are more rules that require classes.

We hope that this section will help developers avoid some common pitfalls in writing Rust code.

## Coding specification content conventions

Identified by the number before the title.

- Identified as `P` for Principle. Numbered as `P.Element.Number`.
- Identified as `G` for Rule (Guideline). The numbering is `G.Element.Number`.
- When there are subdirectories. Number is `P.Element.SubElement.Number` or `G.Element.SubElement.Number`.

Number is incremented from `01`. Where `Element` is the three-letter abbreviation for the key element (corresponding to the secondary catalog in this specification) in the domain knowledge. (Terminology reference: [SEI CERT C Coding Standard](https://wiki.sei.cmu.edu/confluence/display/c/SEI+CERT+C+Coding+Standard))


| Element | Explanation   | Element | Explanation     |
| ------- | ------ | ------- | -------- |
| NAM     | 命名 (Naming)   | CMT     | 注释 (Comment)    |
| FMT     | 格式 (Format)  | TYP     | 数据类型 (Data Type) |
| CNS     | 常量 (Const)   | VAR     | 变量  (Variables)   |
| EXP     | 表达式 (Expression) | CTF     | 控制流程 (Control Flow) |
| REF     | 引用 (Reference)  | PTR     | 指针  (Pointer)   |
| STR     | 字符串 (String) | INT     | 整数 (Integer)    |
| MOD     | 模块  (Module) | CAR     | 包管理  (Cargo) |
| MEM     | 内存 (Memory)  | FUD     | 函数设计 (Function Design) |
| MAC     | 宏  (Macro) | STV     | 静态变量 (Static Variables) |
| GEN    | 泛型 (Generic)  | TRA     | 特质 (Trait) |
| ASY    | 异步 (Async)  | UNS | 非安全 (Unsafe Rust) |
| SAS | 安全抽象 (Safety Abstract) | FFI | 外部函数调用接口 ( Foreign Function Interface ) |
| LAY | 内存布局 (Layout) | ERR | 错误处理 (Error Handle) |
| CLT | 集合  (Collection)  | MTH | 多线程 (Multi Threads) |
| EMB | 嵌入式Rust (Embedded Rust) | FIO      | 输入输出 (In/Out)     |
| SEC | 信息安全 (Security) | SPT | 智能指针 (Smart Pointer) |
| UNT | 单元类型 (Unit) | BOL | 布尔 (Bool) |  
| CHR | 字符类型 (Char) |  FLT | 浮点数 (Float) |  
| SLC | 切片类型 (Slice) |  TUP | 元组 (Tuple) |  
| ARR | 固定长度数组类型 (Array) |  VEC  | 动态长度数组 (Vector)  |  
| SCT | 结构体 (Struct) |  ENM  | 枚举体 (Enum)  |  
| UNI|  联合体 (Union) |   BLN | 标准库内置（BuiltIn）  |  
| OBJ | Trait 对象 (Trait Object)| LFT| 生命周期 (Lifetime) |  
| BOX | `Box<T>` 类型 | DRP  |  析构函数 (Drop) |  
| DCL | 声明宏 (Declarative)  | PRO  |  过程宏 (Procedural) |  
| LCK | 锁同步 (Lock)  | LKF |  无锁 (Lock Free) |  
|  |  | OTH | 其他 (Ohters) |  

## Reference code open source license description

All references to external code in this specification meet the `MIT/Apache/Mozilla public licenses` open source license!