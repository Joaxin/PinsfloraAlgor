# 字符串



### 76. Minimum Window Substring\[H\]

[https://leetcode.com/problems/minimum-window-substring/](https://leetcode.com/problems/minimum-window-substring/)

#### Description

Given a string S and a string T, find the minimum window in S which will contain all the characters in T in complexity O\(n\).

**Example:**

```text
Input: S = "ADOBECODEBANC", T = "ABC"
Output: "BANC"
```

**Note:**

* If there is no such window in S that covers all characters in T, return the empty string `""`.
* If there is such window, you are guaranteed that there will always be only one unique minimum window in S.

#### Solution

[https://leetcode.com/problems/minimum-window-substring/solution/](https://leetcode.com/problems/minimum-window-substring/solution/)

```python

```

### 93. Restore IP Addresses\[M\]

[https://leetcode.com/problems/restore-ip-addresses/](https://leetcode.com/problems/restore-ip-addresses/)

#### Description

Given a string containing only digits, restore it by returning all possible valid IP address combinations.

A valid IP address consists of exactly four integers \(each integer is between 0 and 255\) separated by single points.

**Example:**

```text
Input: "25525511135"
Output: ["255.255.11.135", "255.255.111.35"]
```

#### Solution

```python
class Solution:
    def restoreIpAddresses(self, s: str) -> List[str]:
        ls = len(s)
        if ls == 0 or ls > 12:
            return []
        res = []
        for i in range(1, 4):
            for j in range(1, 4):
                for k in range(1, 4):
                    m = ls - i - j - k
                    if m > 0 and m <= 3:
                        add1 = s[0:i]
                        add2 = s[i:i + j]
                        add3 = s[i + j:i + j + k]
                        add4 = s[i + j + k:]
                        if self.isValid(add1) and self.isValid(add2) and \
                                        self.isValid(add3) and self.isValid(add4):
                            res.append(add1 + '.' + add2 + '.' + add3 + '.' + add4)
        return res

    def isValid(self, add):
        if len(add) == 1:
            return True
        if add[0] == '0':
            return False
        if int(add) <= 255:
            return True
        return False
```

### 97. Interleaving String\[H\]

[https://leetcode.com/problems/interleaving-string/](https://leetcode.com/problems/interleaving-string/)

#### Description

Given _s1_, _s2_, _s3_, find whether _s3_ is formed by the interleaving of _s1_ and _s2_.

**Example 1:**

```text
Input: s1 = "aabcc", s2 = "dbbca", s3 = "aadbbcbcac"
Output: true
```

**Example 2:**

```text
Input: s1 = "aabcc", s2 = "dbbca", s3 = "aadbbbaccc"
Output: false
```

#### Solution

[https://leetcode.com/problems/interleaving-string/solution/](https://leetcode.com/problems/interleaving-string/solution/)

```python

```

### 412. Fizz Buzz\[E\]

[https://leetcode.com/problems/fizz-buzz/](https://leetcode.com/problems/fizz-buzz/)

#### Description

Write a program that outputs the string representation of numbers from 1 to _n_.

But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.

**Example:**

```text
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
```

#### Solution

```python
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        return [str(i) * (i % 3 != 0 and i % 5 != 0) + "Fizz" * (i % 3 == 0) + "Buzz" * (i % 5 == 0) 
                for i in range(1, n + 1)]
```

[https://leetcode.com/problems/fizz-buzz/solution/](https://leetcode.com/problems/fizz-buzz/solution/)

### 1195. Fizz Buzz Multithreaded\[M\]

[https://leetcode.com/problems/fizz-buzz-multithreaded/](https://leetcode.com/problems/fizz-buzz-multithreaded/)

#### Description

Write a program that outputs the string representation of numbers from 1 to _n_, however:

* If the number is divisible by 3, output "fizz".
* If the number is divisible by 5, output "buzz".
* If the number is divisible by both 3 and 5, output "fizzbuzz".

For example, for `n = 15`, we output: `1, 2, fizz, 4, buzz, fizz, 7, 8, fizz, buzz, 11, fizz, 13, 14, fizzbuzz`.

Suppose you are given the following code:

```text
class FizzBuzz {
  public FizzBuzz(int n) { ... }               // constructor
  public void fizz(printFizz) { ... }          // only output "fizz"
  public void buzz(printBuzz) { ... }          // only output "buzz"
  public void fizzbuzz(printFizzBuzz) { ... }  // only output "fizzbuzz"
  public void number(printNumber) { ... }      // only output the numbers
}
```

Implement a multithreaded version of `FizzBuzz` with **four** threads. The same instance of `FizzBuzz` will be passed to four different threads:

1. Thread A will call `fizz()` to check for divisibility of 3 and outputs `fizz`.
2. Thread B will call `buzz()` to check for divisibility of 5 and outputs `buzz`.
3. Thread C will call `fizzbuzz()` to check for divisibility of 3 and 5 and outputs `fizzbuzz`.
4. Thread D will call `number()` which should only output the numbers.

#### Solution

```python

```

