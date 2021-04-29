# 水仙花数 \| Narcissistic Number

### 367. Valid Perfect Square\[E\]

[https://leetcode.com/problems/valid-perfect-square/](https://leetcode.com/problems/valid-perfect-square/)

#### Description

Given a **positive** integer _num_, write a function which returns True if _num_ is a perfect square else False.

**Follow up:** **Do not** use any built-in library function such as `sqrt`.

**Example 1:**

```text
Input: num = 16
Output: true
```

**Example 2:**

```text
Input: num = 14
Output: false
```

**Constraints:**

* `1 <= num <= 2^31 - 1`

#### Solution

```python

```

#### 

水仙花数也被称为超完全数字不变数、自恋数、自幂数、阿姆斯特朗数，它是一个3位数，该数字每个位上数字的立方之和正好等于它本身，例如：$1^3 + 5^3+ 3^3=153$

比如我们寻找一下三位数的水仙花数，

```python
for num in range(100, 1000):
    low = num % 10
    mid = num // 10 % 10
    high = num // 100
    if num == low ** 3 + mid ** 3 + high ** 3:
        print(num)
# 153
# 370
# 371
# 407
```

以上算法十分浅显易懂，我们也可以通过循环写下通解。

```python
for num in range(100,10000):
    sum = 0
    n = len(str(num))

    temp = num
    while temp > 0:
        digit = temp % 10
        sum += digit ** n
        temp //= 10

    if num == sum:
        print(num)
```

```text
153
370
371
407
1634
8208
9474
```

```python
lower=int(input("Please input a number: "))
upper=int(input("Please input a number: "))
sum=0
for num in range(lower,upper):
    l = len(str(num))
    for n in str(num):
        sum=sum+int(n)**l
    if num==sum:
        print(num)
    sum=0
```

