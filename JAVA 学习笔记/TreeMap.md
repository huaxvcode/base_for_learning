---
title: TreeMap
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/TreeMap.pdf
---

# TreeMap

位于头文件：

```java
import java.util.TreeMap;
```

## 按照键从小到大排

```java
var map = new TreeMap<Integer, Integer>((x, y) -> {
    return x - y;
});
```

## 按照键从大到小排

```java
var map = new TreeMap<Integer, Integer>((x, y) -> {
    return y - x;
});
```

## 常用方法

