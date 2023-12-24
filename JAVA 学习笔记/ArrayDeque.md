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

### size

查看元素个数

```java
var len = qu.size();
```

## 作为 Stack 使用

尾进，尾出

### push

尾部添加元素 `x`

```java
qu.push(x);
```

### peek

获取尾部元素

```java
var t = qu.peek();
```

### pop

删除并拿出尾部元素

```java
var t = qu.pop();
```

### size

获取元素个数

```java
var len = qu.size();
```

## 作为 Deque 使用

双端队列，头尾皆可进出

### offerFirst

头部插入元素 `x`

```java
qu.offerFirst(x);
```

### offerLast

尾部插入元素 `y`

```java
qu.offerLast(y);
```

### peekFirst

获取头部元素

```java
var t = qu.peekFirst();
```

### peekLast

获取尾部元素

```java
var t = qu.peekLast();
```

### pollFirst

删除并拿出头部元素

```java
var t = qu.pollFirst();
```

### pollLast

删除并拿出尾部元素

```java
var t = qu.pollLast();
```

### size

获取元素个数

```java
var len = qu.size();
```
