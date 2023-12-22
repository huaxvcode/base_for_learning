---
title: java 的基本整形
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/java 的基本整形.pdf
---

# java 的基本整形

- `int` $4$ 字节
- `long` $8$ 字节
- `short` $2$ 字节
- `byte` $1$ 字节

在 java 中，整形的范围与运行的机器无关，这就解决了软件从一个平台移植到另一个平台的诸多问题

**长整行：**

末尾带有 `L` 或者 `l` 结尾的整数，都属于 `long` 类型，例如：`40000000000l`

**16 进制：**

开头带有 `0x` 的整数，都属于 16 进制数，例如：`0xCAFE`

**8 进制：**

开头带有 `0` 的整数，都属于 8 进制数，例如：`010`

**二进制：**

以 `0b` 开头的 0、1 整数都属于二进制数，例如：`0b1001`

为了更高的可读性，java 允许在为数字字面量**内**加下划线增加可读性，编译器会自动去除这些下划线，例如：

```java
int a = 1_000_000;   // 1000000
int b = 0b1_000_000; // 2 ** 6 = 64
// int c = _1_000_000; 报错
System.out.println(a);
System.out.println(b);
```
