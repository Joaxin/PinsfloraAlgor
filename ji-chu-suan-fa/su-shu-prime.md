# 素数 \| Prime



### 204. Count Primes\[E\]

[https://leetcode.com/problems/count-primes/](https://leetcode.com/problems/count-primes/)

#### Description

Count the number of prime numbers less than a non-negative number, _**n\**_.

**Example:**

```text
Input: 10
Output: 4
Explanation: There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
```

#### Solution

```python
class Solution:
    def countPrimes(self, n: int) -> int:
        isPrime = [True] * n
        for i in range(2, n):
            if i **2 >= n:
                break
            if not isPrime[i]:
                continue
            for j in range(i * i, n, i):
                isPrime[j] = False
        count = 0
        for i in range(2, n):
            if isPrime[i]:
                count += 1
        return count
```

### 素数

#### 验证

最通俗易懂的算法

```python
import math
num = 997
for i in range(2, int(math.sqrt(num)) + 1):
    if num % i == 0:
        print(num, '/', i, '=', num / i, 'is not a prime')
        break
else:
    print(num, 'is a prime.')
```

那求一下前50个素数就可以这样写，

```python
count = 0
num = 2
while count < 50:
    for i in range(2, int(math.sqrt(num)) + 1):
        if num % i == 0:
            break
    else:
        print(num)
        count += 1
    num += 1
```

埃氏法求素数生成1000以内的素数

```python
#!/usr/bin/python

def _odd_iter():
    n = 1
    while True:
        n = n + 2
        yield n

def primes():
    yield 2
    it = _odd_iter()
    while True:
        n = next(it)
        yield n
        it = filter(lambda x, n = n: x % n > 0, it)

for n in primes():
    if n < 1000:
        print(n)
    else:
        break
```

```text
# 埃氏筛法
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

def main():
    for n in primes():
        if n < 1000:
            print(n)
        else:
            break

def _odd_iter():
    n = 1
    while True:
        n = n + 2
        yield n

def _not_divisible(n):
    return lambda x: x % n > 0

def primes():
    yield 2
    it = _odd_iter()
    while True:
        n = next(it)
        yield n
        it = filter(_not_divisible(n), it)

if __name__ == '__main__':
    main()
```

```text
def is_prime(n):
    """判断素数的函数"""
    assert n > 0
    for factor in range(2, int(sqrt(n)) + 1):
        if n % factor == 0:
            return False
    return True if n != 1 else False
```

### 题目

```python
'''
Created on Mon Jun 22 13:04:05 2015
定义一个 prime() 函数求整数n 以内（不包括n）的所有素数（1不是素数），并返回一个按照升序排列的素数列表。
使用递归来实现一个二分查找算法函数bi_search()，该函数实现检索任意一个整数在 prime() 
函数生成的素数列表中位置（索引）的功能，并返回该位置的索引值，若该数不存在则返回 -1。
输入格式:
第一行为正整数 n
接下来若干行为待查找的数字，每行输入一个数字
输出格式：
每行输出相应的待查找数字的索引值

输入样例：
10
2
4
6
7

输出样例：
0
-1
-1
3
'''
```

```python
# -*- coding: utf-8 -*-
import math
primelist = []

def prime(n):
    if n == 2:
        return primelist.append(2)
    for num in range(2, n + 1):
        prime = 1
        for k in range(2, int(math.sqrt(num)) + 1):
            if num % k == 0:
                prime = 0
                break
        if prime == 1:
            primelist.append(num)


def bi_search(prime, primelist, start, end):
    if prime < 2:
        return -1
    if start > end:
        return -1
    mid = (start+end)/2
    if primelist[mid] == prime:
        return mid
    elif primelist[mid] > prime:
        end = mid-1
    else:
        start = mid+1
    return bi_search(prime, primelist, start, end)


number = input()
prime(number)
# print primelist
while True:
    try:
        num = int(raw_input())
    except:
        break
    print bi_search(num, primelist, start=0, end=len(primelist)-1)
```

```python
# 输出指定范围内的素数

# take input from the user
lower = int(input("输入区间最小值: "))
upper = int(input("输入区间最大值: "))

for num in range(lower,upper + 1):
    # 素数大于 1
    if num > 1:
        for i in range(2,num):
            if (num % i) == 0:
                break
        else:
            print(num)
```

```python
from math import sqrt
for n in range(2, 1000):
    for x in range(2, int(sqrt(n)+1)):
        if n % x == 0:
            print(n, '=', x, '*', n//x)
            break
    else:
        print(n, 'is a prime.')
```

