---
title: ArrayList
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/ArrayList.pdf
---

# ArrayList

位于头文件：

```java
import java.util.ArrayList;
```

## 定义一个 ArrayList 对象

方式一：

```java
ArrayList<Integer> a = new ArrayList<Integer>();
```

方式二：

这种方法也称为『菱形语法』，赋值给一个变量 或者 传递给某个方法 或者 作为某个方法的返回值时，编译器会检查这个变量、参数或方法的泛型类型，然后将这个泛型类型放入到菱形 `<>` 中（编译器的自动检查功能）

```java
ArrayList<Integer> a = new ArrayList<>();
```

如果位于局部变量，就有方式三：

前提是 java 10 版本以上

```java
var a = new ArrayList<Integer>();
```

## 常用方法

### add

尾部添加数据 `x`

```java
a.add(x);
```

在下标 `i` 处插入元素 `x`

```java
a.add(i, x);
```

### get

获取下标为 `i` 的内容

```java
var t = a.get(i);
```

### set

修改下标为 `i` 的内容，改为 `x`

```java
a.set(i, x);
```

### size

获取元素个数

```java
var len = a.size();
```

### 排序

升序排列：

```java
Arrays.sort(a, 0, a.size(), (x, y) -> {
    return x - y;
});
```

降序排列：

```java
Arrays.sort(a, 0, a.size(), (x, y) -> {
    return -(x - y);
});
```
