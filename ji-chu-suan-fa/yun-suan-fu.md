# 运算符



### 29. Divide Two Integers\[M\]

[https://leetcode.com/problems/divide-two-integers/](https://leetcode.com/problems/divide-two-integers/)

#### Description

iven two integers `dividend` and `divisor`, divide two integers without using multiplication, division and mod operator.

Return the quotient after dividing `dividend` by `divisor`.

The integer division should truncate toward zero, which means losing its fractional part. For example, `truncate(8.345) = 8` and `truncate(-2.7335) = -2`.

**Example 1:**

```text
Input: dividend = 10, divisor = 3
Output: 3
Explanation: 10/3 = truncate(3.33333..) = 3.
```

**Example 2:**

```text
Input: dividend = 7, divisor = -3
Output: -2
Explanation: 7/-3 = truncate(-2.33333..) = -2.
```

**Note:**

* Both dividend and divisor will be 32-bit signed integers.
* The divisor will never be 0.
* Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: \[−231,  231 − 1\]. For the purpose of this problem, assume that your function **returns 231 − 1 when the division result overflows**.

#### Solution

```python

```

### 371. Sum of Two Integers

[https://leetcode.com/problems/sum-of-two-integers/](https://leetcode.com/problems/sum-of-two-integers/)

#### Description

Calculate the sum of two integers _a_ and _b_, but you are **not allowed** to use the operator `+` and `-`.

**Example 1:**

```text
Input: a = 1, b = 2
Output: 3
```

**Example 2:**

```text
Input: a = -2, b = 3
Output: 1
```

#### Solution

hahaha

```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        return sum([a,b])
```

```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        return operator.add(a, b)
```

Ok, that’s ridiculous and cheating, ok, now do it without using pre-defined functionslet us dive into the bit operators.

[https://leetcode.com/problems/sum-of-two-integers/discuss/84278/A-summary%3A-how-to-use-bit-manipulation-to-solve-problems-easily-and-efficiently](https://leetcode.com/problems/sum-of-two-integers/discuss/84278/A-summary%3A-how-to-use-bit-manipulation-to-solve-problems-easily-and-efficiently)

\[[https://leetcode.com/problems/sum-of-two-integers/discuss/84282/Python-solution-with-no-%22%2B-\*%22-completely-bit-manipulation-guaranteed\]\(https://leetcode.com/problems/sum-of-two-integers/discuss/84282/Python-solution-with-no-"%2B-\*"-completely-bit-manipulation-guaranteed](https://leetcode.com/problems/sum-of-two-integers/discuss/84282/Python-solution-with-no-%22%2B-*%22-completely-bit-manipulation-guaranteed]%28https://leetcode.com/problems/sum-of-two-integers/discuss/84282/Python-solution-with-no-"%2B-*"-completely-bit-manipulation-guaranteed)\)

```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        # 32 bits integer max
        MAX = 0x7FFFFFFF
        # 32 bits interger min
        MIN = 0x80000000
        # mask to get last 32 bits
        mask = 0xFFFFFFFF
        while b != 0:
            # ^ get different bits and & gets double 1s, << moves carry
            a, b = (a ^ b) & mask, ((a & b) << 1) & mask
        # if a is negative, get a's 32 bits complement positive first
        # then get 32-bit positive's Python complement negative
        return a if a <= MAX else ~(a ^ mask)
```

[https://leetcode.com/discuss/111582/java-simple-easy-understand-solution-with-explanation](https://leetcode.com/discuss/111582/java-simple-easy-understand-solution-with-explanation)

[https://leetcode.com/discuss/111705/one-positive-one-negative-case-successful-for-python-rules](https://leetcode.com/discuss/111705/one-positive-one-negative-case-successful-for-python-rules)

In Python this problem is much different because of the negative number.

```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        import ctypes
        sum = 0
        carry = ctypes.c_int32(b)
        while carry.value:
            sum = a ^ carry.value
            carry = ctypes.c_int32(a & carry.value)
            carry.value <<= 1
            a = sum
        return sum
```

### 69. Sqrt\(x\)\[E\]

[https://leetcode.com/problems/sqrtx/](https://leetcode.com/problems/sqrtx/)

#### Description

implement `int sqrt(int x)`.

Compute and return the square root of _x_, where _x_ is guaranteed to be a non-negative integer.

Since the return type is an integer, the decimal digits are truncated and only the integer part of the result is returned.

**Example 1:**

```text
Input: 4
Output: 2
```

**Example 2:**

```text
Input: 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since 
             the decimal part is truncated, 2 is returned.
```

#### Solution

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        return int(math.sqrt(x))
```

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x == 0:
            return 0
        if x < 4:
            return 1
        res = 2 * self.mySqrt(x / 4)
        if (res + 1) * (res + 1) <= x and (res + 1) * (res + 1) >= 0:
            return res + 1
        return  res
```

### 166. Fraction to Recurring Decimal\[M\]

[https://leetcode.com/problems/fraction-to-recurring-decimal/](https://leetcode.com/problems/fraction-to-recurring-decimal/)

#### Description

Given two integers representing the numerator and denominator of a fraction, return the fraction in string format.

If the fractional part is repeating, enclose the repeating part in parentheses.

**Example 1:**

```text
Input: numerator = 1, denominator = 2
Output: "0.5"
```

**Example 2:**

```text
Input: numerator = 2, denominator = 1
Output: "2"
```

**Example 3:**

```text
Input: numerator = 2, denominator = 3
Output: "0.(6)"
```

#### Solution

```python

```

### 368. Largest Divisible Subset\[M\]

[https://leetcode.com/problems/largest-divisible-subset/](https://leetcode.com/problems/largest-divisible-subset/)

#### Description

Given a set of **distinct** positive integers, find the largest subset such that every pair \(Si, Sj\) of elements in this subset satisfies:

Si % Sj = 0 or Sj % Si = 0.

If there are multiple solutions, return any subset is fine.

**Example 1:**

```text
Input: [1,2,3]
Output: [1,2] (of course, [1,3] will also be ok)
```

**Example 2:**

```text
Input: [1,2,4,8]
Output: [1,2,4,8]
```

#### Solution

```python

```



### 50. Pow\(x, n\)\[M\]

[https://leetcode.com/problems/powx-n/](https://leetcode.com/problems/powx-n/)

#### Description

Implement [pow\(_x_, _n_\)](http://www.cplusplus.com/reference/valarray/pow/), which calculates _x_ raised to the power _n_ \(xn\).

**Example 1:**

```text
Input: 2.00000, 10
Output: 1024.00000
```

**Example 2:**

```text
Input: 2.10000, 3
Output: 9.26100
```

**Example 3:**

```text
Input: 2.00000, -2
Output: 0.25000
Explanation: 2-2 = 1/22 = 1/4 = 0.25
```

**Note:**

* -100.0 &lt; _x_ &lt; 100.0
* _n_ is a 32-bit signed integer, within the range \[−231, 231 − 1

#### Solution

```python
class Solution:
    def myPow(self, x: float, n: int) -> float:
        return x**n
```

[https://leetcode.com/discuss/93413/iterative-log-n-solution-with-clear-explanation](https://leetcode.com/discuss/93413/iterative-log-n-solution-with-clear-explanation)

```python
class Solution:
    def myPow(self, x: float, n: int) -> float:
        # 9 = 2^3 + 2^0 = 1001
        # x^9 = x^(2^3)*x(2^0)
        # multiple x^i when i place is 1
        if n == 0:
            return 1
        res ,curr = 1, abs(n)
        while curr > 0:
            if curr & 1 == 1:
                res *= x
            curr >>= 1
            x *= x
        if n < 0:
            return 1 / res
        return  res
```

### 231. Power of Two\[E\]

[https://leetcode.com/problems/power-of-two/](https://leetcode.com/problems/power-of-two/)

#### Description

Given an integer, write a function to determine if it is a power of two.

**Example 1:**

```text
Input: 1
Output: true 
Explanation: 20 = 1
```

**Example 2:**

```text
Input: 16
Output: true
Explanation: 24 = 16
```

**Example 3:**

```text
Input: 218
Output: false
```

#### Solution

```python
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        if n < 0:
            return False
        bin_str = bin(n)
        return sum(map(lambda x: int(x), list(bin_str[2:]))) == 1
```

### 326. Power of Three\[E\]

[https://leetcode.com/problems/power-of-three/](https://leetcode.com/problems/power-of-three/)

#### Description

Given an integer, write a function to determine if it is a power of three.

**Example 1:**

```text
Input: 27
Output: true
```

**Example 2:**

```text
Input: 0
Output: false
```

**Example 3:**

```text
Input: 9
Output: true
```

**Example 4:**

```text
Input: 45
Output: false
```

**Follow up:** Could you do it without using any loop / recursion?

#### Solution

[https://leetcode.com/problems/power-of-three/solution/](https://leetcode.com/problems/power-of-three/solution/)

```python
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
        max3pow = 1162261467
        if n <= 0 or n > max3pow:
            return False
        return max3pow % n == 0
```

### 342. Power of Four\[E\]

[https://leetcode.com/problems/power-of-four/](https://leetcode.com/problems/power-of-four/)

#### Description

Given an integer \(signed 32 bits\), write a function to check whether it is a power of 4.

**Example 1:**

```text
Input: 16
Output: true
```

**Example 2:**

```text
Input: 5
Output: false
```

**Follow up**: Could you solve it without loops/recursion?

#### Solution

```python
class Solution:
    def isPowerOfFour(self, num: int) -> bool:
        # bin(4**0) '0b1'
        # bin(4**1) '0b100'
        # bin(4**2) '0b10000'
        # bin(4**3) '0b1000000'
        return num > 0 and num & (num-1) == 0 and len(bin(num)[3:]) % 2 == 0
```

### 372. Super Pow\[M\]

[https://leetcode.com/problems/super-pow/](https://leetcode.com/problems/super-pow/)

#### Description

Your task is to calculate _a\*\*b_ mod 1337 where _a_ is a positive integer and _b_ is an extremely large positive integer given in the form of an array.

**Example 1:**

```text
Input: a = 2, b = [3]
Output: 8
```

**Example 2:**

```text
Input: a = 2, b = [1,0]
Output: 1024
```

#### Solution

```python
class Solution:
    def __init__(self):
        self.base = 1337

    def superPow(self, a: int, b: List[int]) -> int:
        # One knowledge: ab % k = (a%k)(b%k)%k
        # a^1234567 % k = (a^1234560 % k) * (a^7 % k) % k = (a^123456 % k)^10 % k * (a^7 % k) % k
        if b is None or len(b) == 0:
            return 1
        last_digit = b.pop()
        return self.powmod(self.superPow(a, b), 10) * \
            self.powmod(a, last_digit) % self.base

    def powmod(self, a, k):
        a %= self.base
        result = 1
        for i in range(k):
            result = (result * a) % self.base
        return result
```

