---
title: PriorityQueue
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/PriorityQueue.pdf
---

# PriorityQueue

位于头文件：

```java
import java.util.PriorityQueue;
```

## 小根堆

```java
var qu = new PriorityQueue<Integer>((x, y) -> {
   return x - y; // -1, 0, 1 这样排序，如果 x < y，就是 -1，排前面 
});
```

## 大根堆

```java
var qu = new PriorityQueue<Integer>((x, y) -> {
    return y - x; // -1, 0, 1 这样排序，如果 x > y，就是 -1，排前面
})
```

## 常用方法

### offer

插入元素 `x`

```java
qu.offer(x);
```

### peek

获取堆顶元素

```java
var t = qu.peek();
```

### poll

删除并拿出堆顶元素

```java
var t = qu.poll();
```

### size

获取元素个数

```java
var len = qu.size();
```
