# 转换Conversion



### 6. ZigZag Conversion

[https://leetcode.com/problems/zigzag-conversion/](https://leetcode.com/problems/zigzag-conversion/)

#### Description

The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: \(you may want to display this pattern in a fixed font for better legibility\)

```text
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

```text
string convert(string s, int numRows);
```

**Example 1:**

```text
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

**Example 2:**

```text
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:

P     I    N
A   L S  I G
Y A   H R
P     I
```

#### Solution

[https://leetcode.com/problems/zigzag-conversion/solution/](https://leetcode.com/problems/zigzag-conversion/solution/)

```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if numRows == 1:
            return s
        # calculate period
        p = 2 * (numRows - 1)
        result = [""] * numRows
        for i in range(len(s)):
            floor = i % p
            if floor >= p//2:
                floor = p - floor
            result[floor] += s[i]
        return "".join(result)
```

### 8. String to Integer \(atoi\)

[https://leetcode.com/problems/string-to-integer-atoi/](https://leetcode.com/problems/string-to-integer-atoi/)

#### Description

Implement `atoi` which converts a string to an integer.

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned.

**Note:**

* Only the space character `' '` is considered as whitespace character.
* Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: \[−231, 231 − 1\]. If the numerical value is out of the range of representable values, INT\_MAX \(231 − 1\) or INT\_MIN \(−231\) is returned.

**Example 1:**

```text
Input: "42"
Output: 42
```

**Example 2:**

```text
Input: "   -42"
Output: -42
Explanation: The first non-whitespace character is '-', which is the minus sign.
             Then take as many numerical digits as possible, which gets 42.
```

**Example 3:**

```text
Input: "4193 with words"
Output: 4193
Explanation: Conversion stops at digit '3' as the next character is not a numerical digit.
```

**Example 4:**

```text
Input: "words and 987"
Output: 0
Explanation: The first non-whitespace character is 'w', which is not a numerical 
             digit or a +/- sign. Therefore no valid conversion could be performed.
```

**Example 5:**

```text
Input: "-91283472332"
Output: -2147483648
Explanation: The number "-91283472332" is out of the range of a 32-bit signed integer.
             Thefore INT_MIN (−231) is returned.
```

#### Solution

```python
class Solution:
    def myAtoi(self, str: str) -> int:
        str = str.strip()
        str = re.findall('^[+\-]?\d+', str)
        if not str:
            return 0
        res = int(''.join(str))
        MAX = 2147483647
        MIN = -2147483648
        if res > MAX:
            return MAX
        if res < MIN: 
            return MIN
        return res
```

### 43. Multiply Strings\[M\]

[https://leetcode.com/problems/multiply-strings/](https://leetcode.com/problems/multiply-strings/)

#### Description

Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`, also represented as a string.

**Example 1:**

```text
Input: num1 = "2", num2 = "3"
Output: "6"
```

**Example 2:**

```text
Input: num1 = "123", num2 = "456"
Output: "56088"
```

**Note:**

1. The length of both `num1` and `num2` is &lt; 110.
2. Both `num1` and `num2` contain only digits `0-9`.
3. Both `num1` and `num2` do not contain any leading zero, except the number 0 itself.
4. You **must not use any built-in BigInteger library** or **convert the inputs to integer** directly.

#### Solution

[https://leetcode.com/problems/multiply-strings/discuss/17615/Simple-Python-solution-18-lines](https://leetcode.com/problems/multiply-strings/discuss/17615/Simple-Python-solution-18-lines)

```python
class Solution:
    def multiply(self, num1: str, num2: str) -> str:
        res = [0] * (len(num1) + len(num2))
        for i, v1 in enumerate(reversed(num1)):
            for j, v2 in enumerate(reversed(num2)):
                int1 = ord(v1) - ord('0')
                int2 = ord(v2) - ord('0')
                res[i + j] += int1 * int2
                res[i + j + 1] += res[i + j] // 10
                res[i + j] %= 10
        while len(res) > 1 and res[-1] == 0: res.pop()
        return ''.join(str(v) for v in res)[::-1]
```

### 12. Integer to Roman\[M\]

[https://leetcode.com/problems/integer-to-roman/](https://leetcode.com/problems/integer-to-roman/)

#### Description

Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

```text
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

For example, two is written as `II` in Roman numeral, just two one's added together. Twelve is written as, `XII`, which is simply `X` + `II`. The number twenty seven is written as `XXVII`, which is `XX` + `V` + `II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

* `I` can be placed before `V` \(5\) and `X` \(10\) to make 4 and 9. 
* `X` can be placed before `L` \(50\) and `C` \(100\) to make 40 and 90. 
* `C` can be placed before `D` \(500\) and `M` \(1000\) to make 400 and 900.

Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.

**Example 1:**

```text
Input: 3
Output: "III"
```

**Example 2:**

```text
Input: 4
Output: "IV"
```

**Example 3:**

```text
Input: 9
Output: "IX"
```

**Example 4:**

```text
Input: 58
Output: "LVIII"
Explanation: L = 50, V = 5, III = 3.
```

**Example 5:**

```text
Input: 1994
Output: "MCMXCIV"
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

#### Solution

```python
class Solution:
    def intToRoman(self, num: int) -> str:
        values = [1000, 900, 500, 400,100, 90, 50, 40,10, 9, 5, 4, 1]
        symbols = ["M", "CM", "D", "CD","C", "XC", "L", "XL",
                   "X", "IX", "V", "IV","I"]
        roman = ''
        i = 0
        while num > 0:
            k = num // values[i]
            for j in range(k):
                roman += symbols[i]
                num -= values[i]
            i += 1
        return roman
```

### 13. Roman to Integer\[E\]

[https://leetcode.com/problems/roman-to-integer/](https://leetcode.com/problems/roman-to-integer/)

#### Description

Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

```text
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

For example, two is written as `II` in Roman numeral, just two one's added together. Twelve is written as, `XII`, which is simply `X` + `II`. The number twenty seven is written as `XXVII`, which is `XX` + `V` + `II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

* `I` can be placed before `V` \(5\) and `X` \(10\) to make 4 and 9. 
* `X` can be placed before `L` \(50\) and `C` \(100\) to make 40 and 90. 
* `C` can be placed before `D` \(500\) and `M` \(1000\) to make 400 and 900.

Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

> If I comes before V or X, subtract 1 eg: IV = 4 and IX = 9 // 1 5 - 1 10 If X comes before L or C, subtract 10 eg: XL = 40 and XC = 90 // 10 50 - 10 100 If C comes before D or M, subtract 100 eg: CD = 400 and CM = 900 // 100 500 - 100 1000

**Example 1:**

```text
Input: "III"
Output: 3
```

**Example 2:**

```text
Input: "IV"
Output: 4
```

**Example 3:**

```text
Input: "IX"
Output: 9
```

**Example 4:**

```text
Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
```

**Example 5:**

```text
Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

#### Solution

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        romans = {'I': 1, 'V': 5, 'X': 10,'L':50, 'C':100, 'D':500, 'M':1000}
        i = sum = 0
        l = len(s)
        patterns = ["IV","IX","XL","XC","CD","CM"] # make special patterns

        while i < l:
            if s[i:i+2] in patterns:
                sum += romans[s[i+1]] - romans[s[i]]
                i += 2
            else:
                sum += romans[s[i]]
                i += 1
        return sum
```

```python
import time
start1 = time.process_time()
start2 = time.perf_counter()
def romanToInt(s):
    romans = {'I': 1, 'V': 5, 'X': 10,'L':50, 'C':100, 'D':500, 'M':1000}
    # If I comes before V or X, subtract 1 eg: IV = 4 and IX = 9    // 1 5 - 1 10
    # If X comes before L or C, subtract 10 eg: XL = 40 and XC = 90 // 10 50 - 10 100
    # If C comes before D or M, subtract 100 eg: CD = 400 and CM = 900 // 100 500 - 100 1000
    i = sum = 0
    l = len(s)
    patterns = ["IV","IX","XL","XC","CD","CM"] # make special patterns

    while i < l:
        if s[i:i+2] in patterns:
            sum += romans[s[i+1]] - romans[s[i]]
            i += 2
        else:
            sum += romans[s[i]]
            i += 1
    return sum

print(romanToInt("MCMXCIV"))

end1 = time.process_time()
end2 = time.perf_counter()

print('Running time: %s S / %s MS'%(end1 - start1, end2 - start2))
```

### 91. Decode Ways\[M\]

[https://leetcode.com/problems/decode-ways/](https://leetcode.com/problems/decode-ways/)

#### Description

A message containing letters from `A-Z` is being encoded to numbers using the following mapping:

```text
'A' -> 1
'B' -> 2
...
'Z' -> 26
```

Given a **non-empty** string containing only digits, determine the total number of ways to decode it.

**Example 1:**

```text
Input: "12"
Output: 2
Explanation: It could be decoded as "AB" (1 2) or "L" (12).
```

**Example 2:**

```text
Input: "226"
Output: 3
Explanation: It could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).
```

#### Solution

```python

```

### 405. Convert a Number to Hexadecimal\[E\]

[https://leetcode.com/problems/convert-a-number-to-hexadecimal/](https://leetcode.com/problems/convert-a-number-to-hexadecimal/)

#### Description

Given an integer, write an algorithm to convert it to hexadecimal. For negative integer, \[two’s complement\]\([https://en.wikipedia.org/wiki/Two's\_complement](https://en.wikipedia.org/wiki/Two's_complement)\) method is used.

**Note:**

1. All letters in hexadecimal \(`a-f`\) must be in lowercase.
2. The hexadecimal string must not contain extra leading `0`s. If the number is zero, it is represented by a single zero character `'0'`; otherwise, the first character in the hexadecimal string will not be the zero character.
3. The given number is guaranteed to fit within the range of a 32-bit signed integer.
4. You **must not use \*any\* method provided by the library** which converts/formats the number to hex directly.

**Example 1:**

```text
Input:
26

Output:
"1a"
```

**Example 2:**

```text
Input:
-1

Output:
"ffffffff"
```

#### Solution

```python
class Solution:
    def toHex(self, num: int) -> str:
        if num == 0:
            return '0'
        # letter map
        mp = '0123456789abcdef'
        ans = ''
        for _ in range(8):
            # get last 4 digits
            # num & 1111b
            n = num & 15
            # hex letter for current 1111
            c = mp[n]
            ans = c + ans
            # num = num / 16
            num = num >> 4
        #strip leading zeroes
        return ans.lstrip('0'
```

### 273. Integer to English Words\[H\]

[https://leetcode.com/problems/integer-to-english-words/](https://leetcode.com/problems/integer-to-english-words/)

#### Description

Convert a non-negative integer to its english words representation. Given input is guaranteed to be less than 231 - 1.

**Example 1:**

```text
Input: 123
Output: "One Hundred Twenty Three"
```

**Example 2:**

```text
Input: 12345
Output: "Twelve Thousand Three Hundred Forty Five"
```

**Example 3:**

```text
Input: 1234567
Output: "One Million Two Hundred Thirty Four Thousand Five Hundred Sixty Seven"
```

**Example 4:**

```text
Input: 1234567891
Output: "One Billion Two Hundred Thirty Four Million Five Hundred Sixty Seven Thousand Eight Hundred Ninety One"
```

#### Solution

[https://leetcode.com/problems/integer-to-english-words/discuss/70632/Recursive-Python](https://leetcode.com/problems/integer-to-english-words/discuss/70632/Recursive-Python)

```python
class Solution:
    def numberToWords(self, num: int) -> str:
        to19 = 'One Two Three Four Five Six Seven Eight Nine Ten Eleven Twelve ' \
           'Thirteen Fourteen Fifteen Sixteen Seventeen Eighteen Nineteen'.split()
        tens = 'Twenty Thirty Forty Fifty Sixty Seventy Eighty Ninety'.split()
        thousand = 'Thousand Million Billion'.split()

        def word(num, idx=0):
            if num == 0:
                return []
            if num < 20:
                return [to19[num-1]]
            if num < 100:
                return [tens[num//10-2]] + word(num%10)
            if num < 1000:
                return [to19[num//100-1]] + ['Hundred'] + word(num%100)

            p, r = num//1000, num%1000
            space = [thousand[idx]] if p % 1000 !=0 else []
            return  word(p, idx+1) + space + word(r)
        return ' '.join(word(num)) or 'Zero'
```

