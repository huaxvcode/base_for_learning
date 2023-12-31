---
title: 自动关闭资源的 try 语句块
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/自动关闭资源的 try 语句块.pdf
---

# 自动关闭资源的 try 语句块

示例：

```java
import java.util.*;
import java.io.*;

public class Main {
    public static void main(String[] args) {
        try (var out = new PrintWriter(new OutputStreamWriter(System.out))) {
            for (int i = 1; i <= 9; i ++) {
                for (int j = 1; j <= i; j ++) {
                    out.printf ("%d*%d=%-3d", j, i, i * j);
                }
                out.println();
            }
        }
    }
}
```

这里的 `try` 语句块：

```java
try (var out = new PrintWriter(new OutputStreamWriter(System.out))) {

}
```

或者：

```java
var out = new PrintWriter(new OutputStreamWriter(System.out));
try (out) {

}
```

相当于：

```java
var out = new PrintWriter(new OutputStreamWriter(System.out));
try {
    
}
finally {
    out.close();
}
```

---

如果某类要使用上述功能，得继承 `AutoCloseable` 接口，并实现 `public void close() throws Exception` 方法：

```java
import java.util.*;
import java.io.*;

class IO implements AutoCloseable {
    BufferedReader in;
    PrintWriter out;
    final String space;
    {
        space = "\\s+";
        in = new BufferedReader(new InputStreamReader(System.in));
        out = new PrintWriter(new OutputStreamWriter(System.out));
    }
    @Override
    public void close() throws Exception {
        in.close();
        out.close();
    }
}

public class Main {
    public static void main(String[] args) throws Exception {
        var io = new IO();
        try (io) {
            int n = Integer.parseInt(io.in.readLine().split(io.space)[0]);
            for (int i = 1; i <= n; i ++) {
                for (int j = 1; j <= i; j ++) {
                    io.out.printf ("%d*%d=%-3d", j, i,  i * j);
                }
                io.out.println();
            }
        }
    }
}
```
