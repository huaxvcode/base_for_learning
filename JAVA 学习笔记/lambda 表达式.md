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

java 没有函数这一说法，但是却有函数式接口，即：一个接口中，只存在一个抽象方法时，就可成为函数式接口，所有的函数式接口，都可用 lambda 表达式生成一个函数式接口的对象

---

示例四：

**你甚至可以用现有的方法生成一个函数式接口的对象**

现有的方法：不管是静态方法，还是实例方法都可以

```java
import java.util.*;

interface Rd {
    Random getRd();
}

public class Main {
    public static Random getRd() { return new Random(new Date().getTime()); }
    public Random getRd_() { return new Random(new Date().getTime()); }
    public static void main(String[] args) {
        Rd rd1 = Main::getRd;
        var cmd = new Main();
        Rd rd2 = cmd::getRd_;
        System.out.println(rd1.getRd().nextInt());
        System.out.println(rd2.getRd().nextInt());
    }
}
```

上方示例就使用了静态方法 `Main::getRd` 和实例方法 `cmd::getRd_` 生成了一个 `Rd` 对象

`Main::getRd` 是一个方法的引用，它指示编译器生成一个函数式接口的实例

---

如果函数式接口的抽象方法有如下参数：`(x, y)`

**类名::静态方法** 与 **对象::实例方法** 与 **lambda** 表达式基本等同，抽象方法有多少个参数，就会传入多少个参数给他们，可以将他们看做是抽象方法的一次实现

但是，**类名::实例方法** 与上面的会有些许的不同，就算抽象方法有 $n$ 个参数，但是**类名::实例方法**只会接受后面的 $n - 1$ 个参数，抽象方法的第一个参数会作为对象来调用该实例方法，并将后面的 $n - 1$ 个参数依次传入该方法中，示例：

```java
import java.util.*;
class Max {
    int max(int... args) {
        if (args.length == 0) return Integer.MIN_VALUE;
        int res = args[0];
        for (var x : args) res = x > res ? x : res;
        return res;
    }
}
interface GetMax {
    int max(Max tl, int... args);
}
public class Main {
    public static int max(GetMax itf, int... args) {
        return itf.max(new Max(), args);
    }
    public static void main(String... args) {
        var res = max(Max::max, 2, 3, 1, 4, 5, 2, 3, 10);
        System.out.println(res);
    }
}
```

正如上方的示例，我们观察到：

```java
public static int max(GetMax itf, int... args) {
    return itf.max(new Max(), args);
}
```

接口对象调用抽象方法 `max` 时，传入了参数 `new Max()` 和 `args`，编译器会将这些参数这样传递给 类名::实例方法：`new Max().max(args)`

如果是传递给 类名::静态方法、对象::实例方法、lambda 表达式，就直接传 `max(new Max(), args)`

换句话理解：传入到函数式接口的抽象方法中的参数，会全部依次传入到 **类名::静态方法**、**对象::实例方法**、**lambda 表达式** 中，但对于 **类名::实例方法**，会将第一个参数作为对象来调用该实例方法，然后将剩下的参数依次传入到该实例方法中

---

## 如何使用外部的变量

lambda 表达式内部能调用的外部变量，只能是外面的『事实最终局部变量』和字段

如果是局部变量，就必须是『事实最终局部变量』，但是对字段并没有任何限制要求

『事实最终局部变量』：指那些加了 `final` 修饰的或者没有加 `final` 修饰，但是在使用中没有改变值的局部变量，一经赋值就不再改变值，而且赋值是在创建后立马进行的局部变量

下方代码中，只有注释掉 `pi = 3.141592` 这一行后才不报错：

```java
import java.io.*;
import java.util.*;

interface A {
    void print();
}

public class Main {
    BufferedReader cin;
    PrintWriter cout;

    {
        cin = new BufferedReader(new InputStreamReader(System.in));
        cout = new PrintWriter(new OutputStreamWriter(System.out));

    }
    void solve() {
        double pi = 3.14;
        A t = () -> {
// ☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆
            pi = 3.141592; // 引用的局部变量，必须是『事实最终变量』，但是字段没有限制，所以这句话报错，但是下面两句话的允许的
// ☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆
            cin = new BufferedReader(new InputStreamReader(System.in));
            cout = new PrintWriter(new OutputStreamWriter(System.out));
            cout.println("hello world");
            cout.flush();
        };
        t.print();
    }
    public static void main(String[] args) {
        var cmd = new Main();
        cmd.solve();
    }
}
```

