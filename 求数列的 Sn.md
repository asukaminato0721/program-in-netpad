# 有数列 a<sub>n</sub>, 求其 S<sub>n</sub>

以 a<sub>n</sub> =n<sup>2</sup> 为例

## 核心思想

累加变量 S, 在循环中累加 a<sub>i</sub>

### 状态转移

状态转移是 DP（动态规划）里的概念，此处借用一下

因为画板没有循环，所以需要用迭代模拟。

每次迭代前后，状态发生变化，称其为状态转移。

## 画板实现

1. [参数](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.9.1_%E5%8F%98%E9%87%8F%E5%B0%BA.html) `i = 1`, `S = 0`, `n = 3`
2. [计算](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.9.5_%E6%B5%8B%E9%87%8F.html) `i + 1`
3. [计算](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.9.5_%E6%B5%8B%E9%87%8F.html) `S + i * i`
4. [坐标点](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.1.5_%E5%9D%90%E6%A0%87%E7%82%B9.html) `(S, 0)`
5. [迭代](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.7.8_%E8%BF%AD%E4%BB%A3.html)，次数 `n`，取迭代终像
    | 迭代原像 | 迭代初像  |
    | :------: | :-------: |
    |    i     |   i + 1   |
    |    S     | S + i * i |
6. 迭代终像上取点，[度量纵坐标](https://www.netpad.net.cn/helpOnLine.html#/helpBook/section1/1.4.9.5_%E6%B5%8B%E9%87%8F.html)

## 总结

在迭代里，我们看到从 迭代原像 到 迭代初像，发生了转移。本质是一个状态机。

## 课件网址

<https://www.netpad.net.cn/resource_web/course/#/237501>

n 是迭代次数，对应 S<sub>n</sub>

## 代码实现

### C

```c
#include <stdio.h>
int a(int n)
{
    return n * n;
}
int s(int n)
{
    int S = 0;
    for (size_t i = 1; i <= n; i++)
    {
        S += a(i);
    }
    return S;
}
int main(void)
{
    printf("%d", s(3));
    return 0;
}
```

### Python

```py
def a(n: int) -> int:
    return n**2


def s(n: int) -> int:
    # return sum(a(i) for i in range(1, n+1))
    S = 0
    for i in range(1, n+1):
        S += a(i)
    return S


print(s(3))
```
