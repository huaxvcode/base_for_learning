---
title: final 成员变量
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/final 成员变量.pdf
---

# final 成员变量

final 修饰的成员变量，必须在构造器中初始化，否则会报错

---

下方例子，没有在构造器中初始化，所以程序报错：

```java
public class Main {
    public final int pi;
    public static void main(String[] args) {
        var cmd = new Main();
        cmd.pi = 1234; // 报错
        System.out.println(cmd.pi);
    }
}
```

---

正确写法：

```java
public class Main {
    public final int pi = 1234;
    public static void main(String[] args) {
        var cmd = new Main();
        System.out.println(cmd.pi);
    }
}
```

或者：

```java
public class Main {
    public final int pi;
    public Main() {
        pi = 1234;
    }
    public static void main(String[] args) {
        var cmd = new Main();
        System.out.println(cmd.pi);
    }
}
```
