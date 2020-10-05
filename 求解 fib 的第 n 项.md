# 求解 fib 的第 n 项

用 fib 这个经典例子讲解多参数迭代的要点

## 核心思想

变量互相累加迭代

a<sub>1</sub> = 1, a<sub>2</sub> = 1, a<sub>n</sub> = a<sub>n-1</sub> + a<sub>n-2</sub>

这里用 Python 代码解释

### Python

```py
def fib(n: int):
    a = 0
    b = 1
    for i in range(1, n + 1):
        a, b = b, a + b
        print(a)
fib(5)
```

## 画板实现

1. [参数](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.9.1_%E5%8F%98%E9%87%8F%E5%B0%BA.html) `a = 0`, `b = 1`, `n = 5`
2. [计算](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.9.5_%E6%B5%8B%E9%87%8F.html) `a + b`
3. [坐标点](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.1.5_%E5%9D%90%E6%A0%87%E7%82%B9.html) `(a, 0)`
4. [迭代](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.7.8_%E8%BF%AD%E4%BB%A3.html)，次数 `n`，取迭代终像
    | 迭代原像 | 迭代初像 |
    | :------: | :------: |
    |    a     |    b     |
    |    b     |  a + b   |
5. 迭代终像上取点，[度量横坐标](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.9.5_%E6%B5%8B%E9%87%8F.html)

## 总结

在这个迭代里，我们看到两个变量互相累加对方，得到了 fib 数列的效果。此方法可以拓展到任意线性递推数列的迭代。

## 课件网址

<https://www.netpad.net.cn/resource_web/course/#/237905>

n 是迭代次数，对应 fib<sub>n</sub>

## 代码实现

### C

```c
#include <stdio.h>
void fib(int n)
{
    int a = 0, b = 1;
    for (size_t i = 1; i <= n; i++)
    {
        int tmp = a;
        a = b;
        b = tmp + b;
        printf("%d\n", a);
    }
}
int main(void)
{
    fib(5);
    return 0;
}
```

