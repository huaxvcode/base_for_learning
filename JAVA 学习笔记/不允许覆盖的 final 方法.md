---
title: 不允许覆盖的 final 方法
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/不允许覆盖的 final 方法.pdf
---

# 不允许覆盖的 final 方法

介绍方法的签名：方法的名字和参数列表称为方法的签名

如果子类中定义了一个和超类签名相同的方法，那么子类的这个方法就会覆盖超类中相同签名的方法

在覆盖一个方法时，子类方法不能低于超类方法的可见性

例如：如果在超类中是 public 属性，那么在子类中就不能覆盖成 private 属性

---

如果超类的某方法被 `final` 修饰，则这种方法被继承后不能被覆盖掉

示例：

```java
class A {
    final void print() {
        System.out.println("hello world");
    }
}
class B extends A {
    void print() { // 报错，final 方法不允许覆盖掉
        System.out.println("hello java");
    }
}
```
