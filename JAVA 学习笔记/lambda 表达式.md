---
title: lambda 表达式
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/lambda 表达式.pdf
---

# lambda 表达式

对于只有一个抽象方法的接口，需要这种接口的对象时，就可以提供一个 lambda 表达式

这种接口，也称为函数式接口，只有一个抽象方法的接口

接口的对象：指的是导入了该接口的类的对象，都可以称为接口的对象，都可以通过该接口声明的变量来引用该类的对象

---

对于只有一个抽象方法的接口，需要这种接口的对象时，就可以提供一个 lambda 表达式，示例：

```java
interface Rd {
    Random getRd();
}

public class Main {
    public static Random getRd(Rd rd) {
        return rd.getRd();
    }
    public static void main(String[] args) {
        var rd = getRd(() -> { return new Random(new Date().getTime()); });
        for (int i = 1; i <= 10; i ++) {
            System.out.println(rd.nextInt(10) + 1);
        }
    }
}
```

示例实现了一个接口 `Rd`，内部提供了一个抽象方法 `getRd` 用于获取 `Random` 随机数对象

在主类 `Main` 里面有一个静态方法 `getRd`，该静态方法接收一个接口对象 `Rd rd`，利用这个接口对象调用 `rd.getRd()` 方法，返回一个随机数对象

可以使用 lambda 表达式作为静态方法 `getRd` 的常数，传入进去
