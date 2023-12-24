---
title: TreeSet
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/TreeSet.pdf
---

# TreeSet

元素不可能重复，支持 $O(log(n))$ 时间复杂度查找

位于头文件：

```java
import java.util.TreeSet;
```

## 从小到大排序的红黑树

```java
var set = new TreeSet<Integer>((x, y) -> {
    return x - y;
});
```

## 从大到小排序的红黑树

```java
var set = new TreeSet<Integer>((x, y) -> {
    return y - x;
});
```

## 常用方法

### add

插入元素 `x`

```java
set.add(x);
```

### contains

判断元素 `x` 是否存在

```java
boolean on = set.contains(x);
```

### remove

删除元素 `x`

```java
boolean status = set.remove(x);
```

如果删除成功，就返回 `true`，否则返回 `false`
