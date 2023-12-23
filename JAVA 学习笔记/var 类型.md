---
title: var 类型
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/var 类型.pdf
---

# var 类型

java 10 新功能：

`var` 可以自动推导变量类型，与 c++ 的 `auto` 很类似

使用范围：

- 只能在方法内部中使用
- 定义的变量必须有初值
- 每次只能定义一个变量，不能 `var a = 1, b = 1;` 这样用

```java
public class Main {
    public static void main(String[] args) {
//        var a = 1, b = 1; 错误
        var a = 1;
        var b = 1;
        System.out.println(a + " " + b); // 1 1
    }
}
```

`var` 的存在大大简便了对象的创建，例如：

```java
public class Main {
    public static void main(String[] args) {
        var a = new int[3000000];
    }
}
```
