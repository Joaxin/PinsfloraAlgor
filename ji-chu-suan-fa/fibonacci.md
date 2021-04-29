# Fibonacci



[斐波拉切数列](https://zh.wikipedia.org/wiki/%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0%E5%88%97)

斐波那契数列（Fibonacci sequence），又称黄金分割数列，是意大利数学家莱昂纳多·斐波那契（Leonardoda Fibonacci）在《计算之书》中提出一个在理想假设条件下兔子成长率的问题而引入的数列，所以这个数列也被戏称为"兔子数列"。斐波那契数列的特点是数列的前两个数都是1，从第三个数开始，每个数都是它前面两个数的和，形如：1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...。斐波那契数列在现代物理、准晶体结构、化学等领域都有直接的应用。

The following code demonstrates how to implement a so-called Fibonacci sequence.

${\displaystyle F\_{0}=0}$

${\displaystyle F\_{1}=1}$

${\displaystyle F_{n}=F_{n-1}+F\_{n-2}}\({n}\geq{2}\)$

比较通熟易懂的方法,

```python
a = 0
b = 1
for _ in range(20):
    a, b = b, a + b
    print(a, end=' ')
```

```python
def fib(n): 
    if n == 1 or n == 2: 
        return 1 
    else: 
        i = 2 
        f1 = 1 
        f2 = 1 
    while(i < n): 
            f3 = f1 + f2 
            f1 = f2 
            f2 = f3 
            i = i + 1 
    return f3
fib(10)
# 55
```

递归

```python
def fib(n): 
    if n == 1 or n == 2: 
        return 1 
    else:
        return fib(n-1) + fib(n-2)

fib(10)
# 55
```

```python
## 动态规划 - 适用于有重叠子问题和最优子结构性质的问题
## 使用动态规划方法所耗时间往往远少于朴素解法(用空间换取时间)
def fib(num, temp={}):
    """用递归计算Fibonacci数"""
    if num in (1, 2):
        return 1
    try:
        return temp[num]
    except KeyError:
        temp[num] = fib(num - 1) + fib(num - 2)
    return temp[num]
fib(10)
```

### Generators

```python
import sys

def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
        yield a

for value in fibonacci(10):
    print(value, end = " ")
```

```python
import sys

def fibonacci(n):
    a, b, counter = 1, 1, 1
    while True:
        if (counter > n):
            return
        yield a
        a, b = b, a + b
        counter += 1

f = fibonacci(10)

while True:
    try:
        print(next(f), end=" ")
    except StopIteration as e:
        print('Generator return value:', e.value)
        break

# 1 1 2 3 5 8 13 21 34 55
```

### OOP

```python
class Fib(object):

    def __init__(self):
        self.a, self.b = 0, 1

    def __iter__(self):
        return self

    def __next__(self):
        self.a, self.b = self.b, self.a + self.b
        if self.a > 100:
            raise StopIteration()
        return self.a

    def __getattr__(self, attr):
        if attr == 'age':
            return lambda: 25
        raise AttributeError('\'Student\' object has no attribute \'%s\'' % attr)

# for n in Fib():
#     print(n)
f = Fib()
print(f.age())
```

```python
class Fib(object):

    def __getitem__(self, n):
        if isinstance(n, int):  # n是索引
            a, b = 1, 1
            for x in range(n):
                a, b = b, a + b
            return a
        if isinstance(n, slice):  # n是切片
            start = n.start
            stop = n.stop
            if start is None:
                start = 0
            a, b = 1, 1
            L = []
            for x in range(stop):
                if x >= start:
                    L.append(a)
                a, b = b, a + b
            return L

f = Fib()
print(f[5:8])
```

```python
def fib(num):
    """生成器"""
    a, b = 0, 1
    for _ in range(num):
        a, b = b, a + b
        yield a


class Fib(object):
    """迭代器"""

    def __init__(self, num):
        self.num = num
        self.a, self.b = 0, 1
        self.idx = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.idx < self.num:
            self.a, self.b = self.b, self.a + self.b
            self.idx += 1
            return self.a
        raise StopIteration()
```

```python
    """
迭代器 - __iter__ / __next__
itertools - 生成可迭代序列的工具模块
"""
import itertools

from math import sqrt


def is_prime(num):
    """判断素数"""
    for factor in range(2, int(sqrt(num)) + 1):
        if num % factor == 0:
            return False
    return True


class PrimeIter(object):
    """素数迭代器"""

    def __init__(self, min_value, max_value):
        assert 2 <= min_value <= max_value
        self.min_value = min_value - 1
        self.max_value = max_value

    def __iter__(self):
        return self

    def __next__(self):
        self.min_value += 1
        while self.min_value <= self.max_value:
            if is_prime(self.min_value):
                return self.min_value
            self.min_value += 1
        raise StopIteration()


class FibIter(object):
    """斐波那契数迭代器"""

    def __init__(self, num):
        self.num = num
        self.a, self.b = 0, 1
        self.idx = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.idx < self.num:
            self.a, self.b = self.b, self.a + self.b
            self.idx += 1
            return self.a
        raise StopIteration()


def main():
    # for val in itertools.permutations('ABCD'):
    #     print(val)
    # for val in itertools.combinations('ABCDE', 3):
    #     print(val)
    # for val in itertools.product('黑红梅方', range(1, 14)):
    #     print(val)
    # fib_iter = FibIter(20)
    # print('===>', next(fib_iter))
    # print('===>', next(fib_iter))
    # for val in fib_iter:
    #     print(val)
    prime_iter = PrimeIter(2, 100000)
    for val in prime_iter:
        print(val)


if __name__ == '__main__':
    main()
```

### 509. Fibonacci Number\[E\]

[https://leetcode.com/problems/fibonacci-number/](https://leetcode.com/problems/fibonacci-number/)

#### Description

he **Fibonacci numbers**, commonly denoted `F(n)` form a sequence, called the **Fibonacci sequence**, such that each number is the sum of the two preceding ones, starting from `0` and `1`. That is,

```text
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), for N > 1.
```

Given `N`, calculate `F(N)`.

**Example 1:**

```text
Input: 2
Output: 1
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.
```

**Example 2:**

```text
Input: 3
Output: 2
Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.
```

**Example 3:**

```text
Input: 4
Output: 3
Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.
```

**Note:**

0 ≤ `N` ≤ 30.

#### Solution

```python
class Solution:
    def fib(self, N: int) -> int:
        if N == 0 or N == 1: 
            return N
        fib = [0, 1, 0]
        for i in range(2, N + 1):
            fib[2] = fib[0] + fib[1]
            fib[0], fib[1] = fib[1], fib[2]
        return fib[-1]
```

```python
def main():
    f = [1 , 1]
    for i in range(2, 20):
        f += [f[i - 1] + f[i - 2]]
        # f.append(f[i - 1] + f[i - 2])
    for val in f:
        print(val, end=' ')
```

