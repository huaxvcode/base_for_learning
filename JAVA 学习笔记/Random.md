---
title: Random
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/Random.pdf
---

# Random

在头文件：

```java
import java.util.Random;
```

## 常用方法

### 构造对象

方式一：

```java
var rd = new Random();
```

方式二：随机种子

```java
var rd = new Random(new Date().getTime());
```

### nextInt

生成 `int` 范围内的随机整数：

```java
var t = rd.nextInt();
```

生成 `[0, 10)` 范围内的随机整数：

```java
var t = rd.nextInt(10);
```

### nextLong

生成 `long` 范围内的随机整数：

```java
var t = rd.nextLong();
```

生成 `[0, 10)` 范围内的随机整数：

```java
var t = rd.nextLong(10);
```

### nextFloat

生成 `[0.0, 1.0]` 范围内的随机 `float` 类型

```java
var t = rd.nextFloat();
```

### nextDouble

生成 `[0.0, 1.0]` 范围内的随机 `double` 类型

```java
var t = rd.nextDouble();
```

### nextBoolean

```java
var t = rd.nextBoolean();
```
