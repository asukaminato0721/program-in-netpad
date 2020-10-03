# 有数列 a<sub>n</sub>, 求其 S<sub>n</sub>

以 a<sub>n</sub> =n<sup>2</sup> 为例

## C

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

## Python

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

## 核心思想

累加变量 S, 在循环中累加 a<sub>i</sub>

## 状态转移

状态转移是 DP（动态规划）里的概念，此处借用一下

因为画板没有循环，所以需要用迭代模拟。

每次迭代前后，状态发生变化，称其为状态转移。

## 画板实现

1. 参数 `i = 1`, `S = 0`, `n = 3`
2. 计算 `i + 1`
3. 计算 `S + i * i`
4. 坐标点 `(S, 0)`
5. 迭代，次数 `n`，取迭代终像
    | 迭代原像 | 迭代初像  |
    | :------: | :-------: |
    |    i     |   i + 1   |
    |    S     | S + i * i |
6. 迭代终像上取点，度量纵坐标

## 总结

在迭代里，我们看到从 迭代原像 到 迭代初像，发生了转移。本质是一个状态机。

## 课件网址

<https://www.netpad.net.cn/resource_web/course/#/237501>

n 是迭代次数，对应 S<sub>n</sub>
