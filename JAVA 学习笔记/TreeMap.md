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

### put

插入键值对 `x:y`

```java
map.put(x, y);
```

### containsKey

判断键 `x` 是否存在

```java
boolean on = map.containsKey(x);
```

### get

获取键 `x` 对应的值

```java
var y = map.get(x);
```

### remove

删除某键值对

```java
boolean status = map.remove(x);
```

如果删除成功，`status = true`，否则 `status = false`
