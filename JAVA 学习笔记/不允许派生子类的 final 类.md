---
title: 不允许派生子类的 final 类
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/不允许派生子类的 final 类.pdf
---

# 不允许派生子类的 final 类

`final` 类不允许派生出子类，换句话说就是不允许任何类继承 `final` 类

`final` 类也称为最终类，即：不再允许继承下去

`final` 类中的方法，自动地成为 `final` 方法
 
示例：

```java
final class A {}
class B extends A {} // 报错
```
