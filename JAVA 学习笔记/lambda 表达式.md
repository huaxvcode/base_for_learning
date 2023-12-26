---
title: lambda 表达式
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/lambda 表达式.pdf
---

# lambda 表达式

**对于只有一个抽象方法的接口，需要这种接口的对象时，就可以提供一个 lambda 表达式**

这种接口，也称为函数式接口，只有一个抽象方法的接口

接口的对象：指的是导入了该接口的类的对象，都可以称为接口的对象，都可以通过该接口声明的变量来引用该类的对象

---

对于只有一个抽象方法的接口，需要这种接口的对象时，就可以提供一个 lambda 表达式

示例一：

```java
interface Rd {
    Random getRd();
}

public class Main {
    public static Random getRd(Rd rd) {
        return rd.getRd();
    }
    public static void main(String[] args) {
        var rd = getRd(() -> { return new Random(new Date().getTime()); });
        for (int i = 1; i <= 10; i ++) {
            System.out.println(rd.nextInt(10) + 1);
        }
    }
}
```

示例实现了一个接口 `Rd`，内部提供了一个抽象方法 `getRd` 用于获取 `Random` 随机数对象

在主类 `Main` 里面有一个静态方法 `getRd`，该静态方法接收一个接口对象 `Rd rd`，利用这个接口对象调用 `rd.getRd()` 方法，返回一个随机数对象

可以使用 lambda 表达式作为静态方法 `getRd` 的常数，传入进去

---

示例二：

自定义接口排序规则，实现快速排序：

```java
import java.util.*;

interface Cmp {
    int cmp(int x, int y);
}

public class Main {
    // 利用接口比较，实现一个快速排序
    public static void sort(int[] a, int l, int r, Cmp cmp) {
        if (l >= r) return;
        int mid = (l + r) >> 1;
        int x = a[mid];
        int i = l - 1, j = r + 1;
        while (i < j) {
            while (cmp.cmp(a[++ i], x) < 0);
            while (cmp.cmp(x, a[-- j]) < 0);
            if (i < j) {
                var t = a[i]; a[i] = a[j]; a[j] = t;
            }
        }
        sort(a, l, j, cmp);
        sort(a, j + 1, r, cmp);
    }

    public static void main(String[] args) {
        int n = 15;
        int[] a = new int[n + 10];
        var rd = new Random(new Date().getTime());
        for (int i = 1; i <= n; i ++) a[i] = rd.nextInt(10) + 1;
        System.out.print("原数组为：");
        for (int i = 1; i <= n; i ++) System.out.print(a[i] + " ");
        System.out.println();
        sort(a, 1, n, (x, y) -> {
            return y - x;
        });
        System.out.print("逆序排列：");
        for (int i = 1; i <= n; i ++) System.out.print(a[i] + " ");
        System.out.println();
    }
}
```

---

示例三：

**接口变量可以直接指向 lambda 表达式**

```java
import java.util.*;

interface Rd {
    Random getRd();
}

public class Main {
    public static void main(String[] args) {
        Rd rd = () -> { return new Random(new Date().getTime()); };
        System.out.println(rd.getRd().nextInt());
    }
}
```

再例如，如果接口中存在静态字段呢？

静态字段在接口中都默认是 `public static final` 类型

```java
import java.util.*;

interface Rd {
    double pi = 3.14159265358979323;
    Random getRd();
}

public class Main {
    public static void main(String[] args) {
        Rd rd = () -> { return new Random(new Date().getTime()); };
        System.out.println(rd.getRd().nextInt());

        System.out.println(rd.pi);
    }
}
```

程序输出：

```
-150451432
3.141592653589793
```

**用 lambda 表达式生成的接口对象，不仅完善了抽象方法的功能，还保留了静态字段的内容，倒不如说，静态字段的内容为所有接口对象所共享**

---

java 没有函数这一说法，但是却有函数式接口，即：一个接口中，只存在一个抽象方法时，就可成为函数式接口，所有的函数式接口，都可用 lambda 表达式实现一个对象
