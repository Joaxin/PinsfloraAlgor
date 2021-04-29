# 二进制Binary

### 67. Add Binary\[E\]

[https://leetcode.com/problems/add-binary/](https://leetcode.com/problems/add-binary/)

#### Description

Given two binary strings, return their sum \(also a binary string\).

The input strings are both **non-empty** and contains only characters `1` or `0`.

**Example 1:**

```text
Input: a = "11", b = "1"
Output: "100"
```

**Example 2:**

```text
Input: a = "1010", b = "1011"
Output: "10101"
```

**Constraints:**

* Each string consists only of `'0'` or `'1'` characters.
* `1 <= a.length, b.length <= 10^4`
* Each string is either `"0"` or doesn't contain any leading zero.

#### Solution

```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        return bin(int(a,2)+int(b,2))[2:]
```

### 401. Binary Watch\[E\]

[https://leetcode.com/problems/binary-watch/](https://leetcode.com/problems/binary-watch/)

#### Description

A binary watch has 4 LEDs on the top which represent the **hours** \(**0-11**\), and the 6 LEDs on the bottom represent the **minutes** \(**0-59**\).

Each LED represents a zero or one, with the least significant bit on the right.

![img](https://upload.wikimedia.org/wikipedia/commons/8/8b/Binary_clock_samui_moon.jpg)

For example, the above binary watch reads "3:25".

Given a non-negative integer _n_ which represents the number of LEDs that are currently on, return all possible times the watch could represent.

**Example:**

```text
Input: n = 1
Return: ["1:00", "2:00", "4:00", "8:00", "0:01", "0:02", "0:04", "0:08", "0:16", "0:32"]
```

**Note:**

* The order of output does not matter.
* The hour must not contain a leading zero, for example "01:00" is not valid, it should be "1:00".
* The minute must be consist of two digits and may contain a leading zero, for example "10:2" is not valid, it should be "10:02".

#### Solution

```python

```

### 89. Gray Code\[M\]

[https://leetcode.com/problems/gray-code/](https://leetcode.com/problems/gray-code/)

#### Description

The gray code is a binary numeral system where two successive values differ in only one bit.

Given a non-negative integer _n_ representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.

**Example 1:**

```text
Input: 2
Output: [0,1,3,2]
Explanation:
00 - 0
01 - 1
11 - 3
10 - 2

For a given n, a gray code sequence may not be uniquely defined.
For example, [0,2,3,1] is also a valid gray code sequence.

00 - 0
10 - 2
11 - 3
01 - 1
```

**Example 2:**

```text
Input: 0
Output: [0]
Explanation: We define the gray code sequence to begin with 0.
             A gray code sequence of n has size = 2n, which for n = 0 the size is 20 = 1.
             Therefore, for n = 0 the gray code sequence is [0].
```

#### Solution

```python
class Solution:
    def grayCode(self, n: int) -> List[int]:
        res = [0]
        for i in range(n):
            for j in reversed(range(len(res))):
                res.append(res[j] + (1 << i))
        return res
```

### 338. Counting Bits\[\]

[https://leetcode.com/problems/counting-bits/](https://leetcode.com/problems/counting-bits/)

#### Description

Given a non negative integer number **num**. For every numbers **i** in the range **0 ≤ i ≤ num** calculate the number of 1's in their binary representation and return them as an array.

**Example 1:**

```text
Input: 2
Output: [0,1,1]
```

**Example 2:**

```text
Input: 5
Output: [0,1,1,2,1,2]
```

**Follow up:**

* It is very easy to come up with a solution with run time **O\(n\*sizeof\(integer\)\)**. But can you do it in linear time **O\(n\)** /possibly in a single pass?
* Space complexity should be **O\(n\)**.
* Can you do it like a boss? Do it without using any builtin function like **\_\_builtin\_popcount** in c++ or in any other language.

#### Solution

```python
class Solution:
    def countBits(self, num: int) -> List[int]:
        res = [0] * (num + 1)
        for i in range(1, num + 1):
            # res[left:last] + last bit
            res[i] = res[i >> 1] + (i & 1)
        return res
```

