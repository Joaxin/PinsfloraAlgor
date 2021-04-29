# 距离Distance



### 191. Number of 1 Bits\[E\]

[https://leetcode.com/problems/number-of-1-bits/](https://leetcode.com/problems/number-of-1-bits/)

#### Description

Write a function that takes an unsigned integer and return the number of '1' bits it has \(also known as the [Hamming weight](http://en.wikipedia.org/wiki/Hamming_weight)\).

**Example 1:**

```text
Input: 00000000000000000000000000001011
Output: 3
Explanation: The input binary string 00000000000000000000000000001011 has a total of three '1' bits.
```

**Example 2:**

```text
Input: 00000000000000000000000010000000
Output: 1
Explanation: The input binary string 00000000000000000000000010000000 has a total of one '1' bit.
```

**Example 3:**

```text
Input: 11111111111111111111111111111101
Output: 31
Explanation: The input binary string 11111111111111111111111111111101 has a total of thirty one '1' bits.
```

**Note:**

* Note that in some languages such as Java, there is no unsigned integer type. In this case, the input will be given as signed integer type and should not affect your implementation, as the internal binary representation of the integer is the same whether it is signed or unsigned.
* In Java, the compiler represents the signed integers using \[2's complement notation\]\([https://en.wikipedia.org/wiki/Two's\_complement](https://en.wikipedia.org/wiki/Two's_complement)\). Therefore, in **Example 3** above the input represents the signed integer `-3`.

**Follow up**:

If this function is called many times, how would you optimize it?

#### Solution

[https://leetcode.com/problems/number-of-1-bits/submissions/](https://leetcode.com/problems/number-of-1-bits/submissions/)

```python
class Solution:
    def hammingWeight(self, n: int) -> int:
        count = 0
        while n:
            n &= n - 1
            count += 1
        return count
```

### 461. Hamming Distance\[E\]

[https://leetcode.com/problems/divide-two-integers/](https://leetcode.com/problems/divide-two-integers/)

#### Description

The [Hamming distance](https://en.wikipedia.org/wiki/Hamming_distance) between two integers is the number of positions at which the corresponding bits are different.

Given two integers `x` and `y`, calculate the Hamming distance.

**Note:** 0 ≤ `x`, `y` &lt; 231.

**Example:**

```text
Input: x = 1, y = 4

Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

The above arrows point to positions where the corresponding bits are different.
```

#### Solution

```python
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        return bin(x ^ y).count('1')
```

