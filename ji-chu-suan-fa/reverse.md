# Reverse

### Python的Reverse方法

```python
from io import StringIO


def reverse_str1(str):
    return str[::-1]


def reverse_str2(str):
    if len(str) <= 1:
        return str
    return reverse_str2(str[1:]) + str[0:1]


def reverse_str3(str):
    # StringIO对象是Python中的可变字符串
    # 不应该使用不变字符串做字符串连接操作 因为会产生很多无用字符串对象
    rstr = StringIO()
    str_len = len(str)
    for index in range(str_len - 1, -1, -1):
        rstr.write(str[index])
    return rstr.getvalue()


def reverse_str4(str):
    return ''.join(str[index] for index in range(len(str) - 1, -1, -1))


def reverse_str5(str):
    # 将字符串处理成列表
    str_list = list(str)
    str_len = len(str)
    # 使用zip函数将两个序列合并成一个产生元组的迭代器
    # 每次正好可以取到一前一后两个下标来实现元素的交换
    for i, j in zip(range(str_len // 2), range(str_len - 1, str_len // 2, -1)):
        str_list[i], str_list[j] = str_list[j], str_list[i]
    # 将列表元素连接成字符串
    return ''.join(str_list)
```

### 7. Reverse Integer\[E\]

[https://leetcode.com/problems/reverse-integer/solution/](https://leetcode.com/problems/reverse-integer/solution/)

#### Description

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**

```text
Input: 123
Output: 321
```

**Example 2:**

```text
Input: -123
Output: -321
```

**Example 3:**

```text
Input: 120
Output: 21
```

**Note:** Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: \[$−2^{31}, 2^{31} − 1$\]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

#### Solution

[https://leetcode.com/problems/reverse-integer/solution/](https://leetcode.com/problems/reverse-integer/solution/)

```python
class Solution:
    def reverse(self, x: int) -> int:
        res, sig = 0, 1
        if x < 0:
            sig = -1
            x = -1 * x
        while x > 0:
            res = res * 10 + x % 10
            if res > 2**31 - 1:
                return 0
            x //= 10
        return res * sig
```

```python
class Solution:
    def reverse(self, x: int) -> int:
        x = int(str(x)[::-1]) if x >= 0 else - int(str(-x)[::-1])
        return x if x < 2**31 - 1 and x >= -2**31 else 0
```

### 190. Reverse Bits

[https://leetcode.com/problems/reverse-bits/](https://leetcode.com/problems/reverse-bits/)

#### Description

Reverse bits of a given 32 bits unsigned integer.

**Example 1:**

```text
Input: 00000010100101000001111010011100
Output: 00111001011110000010100101000000
Explanation: The input binary string 00000010100101000001111010011100 represents the unsigned integer 43261596, so return 964176192 which its binary representation is 00111001011110000010100101000000.
```

**Example 2:**

```text
Input: 11111111111111111111111111111101
Output: 10111111111111111111111111111111
Explanation: The input binary string 11111111111111111111111111111101 represents the unsigned integer 4294967293, so return 3221225471 which its binary representation is 10111111111111111111111111111111.
```

**Note:**

* Note that in some languages such as Java, there is no unsigned integer type. In this case, both input and output will be given as signed integer type and should not affect your implementation, as the internal binary representation of the integer is the same whether it is signed or unsigned.
* In Java, the compiler represents the signed integers using \[2's complement notation\]\([https://en.wikipedia.org/wiki/Two's\_complement](https://en.wikipedia.org/wiki/Two's_complement)\). Therefore, in **Example 2** above the input represents the signed integer `-3` and the output represents the signed integer `-1073741825`.

**Follow up**:

If this function is called many times, how would you optimize it?

#### Solution

```python
def reverseBits(self, n):
    return int(bin(n)[2:].zfill(32)[::-1], 2)
```

[https://leetcode.com/problems/reverse-bits/solution/](https://leetcode.com/problems/reverse-bits/solution/)

```python
class Solution:
    def reverseBits(self, n: int) -> int:
        ret, power = 0, 31
        while n:
            ret += (n & 1) << power
            n = n >> 1
            power -= 1
        return ret
```

### 557. Reverse Words in a String III\[E\]

[https://leetcode.com/problems/reverse-words-in-a-string-iii/](https://leetcode.com/problems/reverse-words-in-a-string-iii/)

#### Description

Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

**Example 1:**

```text
Input: "Let's take LeetCode contest"
Output: "s'teL ekat edoCteeL tsetnoc"
```

**Note:** In the string, each word is separated by single space and there will not be any extra space in the string.

#### Solution

[https://leetcode.com/problems/reverse-words-in-a-string-iii/solution/](https://leetcode.com/problems/reverse-words-in-a-string-iii/solution/)

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return ' '.join([word[::-1] for word in s.split(' ')])
```

### 150. Evaluate Reverse Polish Notation\[M\]

[https://leetcode.com/problems/evaluate-reverse-polish-notation/](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

#### Description

Evaluate the value of an arithmetic expression in [Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation).

Valid operators are `+`, `-`, `*`, `/`. Each operand may be an integer or another expression.

**Note:**

* Division between two integers should truncate toward zero.
* The given RPN expression is always valid. That means the expression would always evaluate to a result and there won't be any divide by zero operation.

**Example 1:**

```text
Input: ["2", "1", "+", "3", "*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9
```

**Example 2:**

```text
Input: ["4", "13", "5", "/", "+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6
```

**Example 3:**

```text
Input: ["10", "6", "9", "3", "+", "-11", "*", "/", "*", "17", "+", "5", "+"]
Output: 22
Explanation: 
  ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
```

#### Solution

```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        for t in tokens:
            try:
                temp = int(t)
                stack.append(temp)
            except:
                b = stack.pop()
                a = stack.pop()
                if t == "+":
                    a += b
                elif t == "-":
                    a -= b
                elif t == "*":
                    a *= b
                else:
                    a = int(a * 1.0 / b)
                stack.append(a)
        return stack[-1]
```

### 344. Reverse String\[E\]

[https://leetcode.com/problems/divide-two-integers/](https://leetcode.com/problems/divide-two-integers/)

#### Description

Write a function that reverses a string. The input string is given as an array of characters `char[]`.

Do not allocate extra space for another array, you must do this by **modifying the input array** [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) with O\(1\) extra memory.

You may assume all the characters consist of [printable ascii characters](https://en.wikipedia.org/wiki/ASCII#Printable_characters).

**Example 1:**

```text
Input: ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

**Example 2:**

```text
Input: ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

#### Solution

[https://leetcode.com/problems/reverse-string/solution/](https://leetcode.com/problems/reverse-string/solution/)

```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """        
        s[:] = s[::-1]
```

### 345. Reverse Vowels of a String\[E\]

[https://leetcode.com/problems/reverse-vowels-of-a-string/](https://leetcode.com/problems/reverse-vowels-of-a-string/)

#### Description

Write a function that takes a string as input and reverse only the vowels of a string.

**Example 1:**

```text
Input: "hello"
Output: "holle"
```

**Example 2:**

```text
Input: "leetcode"
Output: "leotcede"
```

**Note:** The vowels does not include the letter "y".

#### Solution

```python
class Solution:
    def reverseVowels(self, s: str) -> str:
        str_index = []
        vowel = []
        res = []
        pos = -1
        for index, value in enumerate(s):
            if value in 'aeiouAEIOU':
                str_index.append(-1)
                vowel.append(value)
            else:
                str_index.append(index)
        for index in str_index:
            if index < 0:
                res.append(vowel[pos])
                pos -= 1
            else:
                res.append(s[index])
        return ''.join(res)
```

