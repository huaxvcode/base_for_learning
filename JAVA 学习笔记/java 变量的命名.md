---
title: java 变量的命名
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/java 变量的命名.pdf
---

# java 变量的命名

与 c++ 语言的变量命令规则基本一致，但又有些许不同

java 语言允许变量名中出现 `$` 字符，并且不允许单个 `_` 作为变量名

---

从 java 10 开始，**对于局部的变量**，如果可以从变量的初始值推断出它的类型，就不再需要声明类型，例如：

```java
public class Main {
    public static void main(String[] args) {
        var a = 1000;
        var b = 3.14;
        System.out.println(a);
        System.out.println(b);
    }
}
```

---

**常量：**

在 java 中，利用 `final` 指示常量，一经赋值，就不能再更改，示例：

```java
public class Main {
    public static void main(String[] args) {
        final double pi;
        pi = 3.14159265;
        System.out.println(pi);
    }
}
```

和 c++ 的 `const` 又有点不太类似，`const` 要求变量生成生命周期后就不能再被赋值

但是 `java` 允许变量生成生命周期后再赋值，只不过只能赋值一次后就会被锁上
