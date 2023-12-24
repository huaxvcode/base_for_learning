---
title: ArrayDeque
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/ArrayDeque.pdf
---

# ArrayDeque

位于头文件：

```java
import java.util.ArrayDeque;
```

## 创建方式

```java
// 方式 1：
ArrayDeque<Integer> qu = new ArrayDeque<Integer>();

// 方式 2：
ArrayDeque<Integer> qu = new ArrayDeque<>();

// 方式 3：java 10 版本以上，且局部变量
var qu = new ArrayDeque<Integer>();

```

## 作为 Queue 使用

尾进，头出

### offer

尾部添加元素 `x`

```java
qu.offer(x);
```

### peek

获取头部元素

```java
var t = qu.peek();
```

### pull

删除并拿出头部元素

```java
var t = qu.poll();
```
