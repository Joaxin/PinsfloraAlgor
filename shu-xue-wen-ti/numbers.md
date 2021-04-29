# Numbers

### 65. Valid Number\[H\]

[https://leetcode.com/problems/valid-number/](https://leetcode.com/problems/valid-number/)

#### Description

Validate if a given string can be interpreted as a decimal number.

Some examples: `"0"` =&gt; `true` `" 0.1 "` =&gt; `true` `"abc"` =&gt; `false` `"1 a"` =&gt; `false` `"2e10"` =&gt; `true` `" -90e3 "` =&gt; `true` `" 1e"` =&gt; `false` `"e3"` =&gt; `false` `" 6e-1"` =&gt; `true` `" 99e2.5 "` =&gt; `false` `"53.5e93"` =&gt; `true` `" --6 "` =&gt; `false` `"-+3"` =&gt; `false` `"95a54e53"` =&gt; `false`

**Note:** It is intended for the problem statement to be ambiguous. You should gather all requirements up front before implementing one. However, here is a list of characters that can be in a valid decimal number:

* Numbers 0-9
* Exponent - "e"
* Positive/negative sign - "+"/"-"
* Decimal point - "."

Of course, the context of these characters also matters in the input.

**Update \(2015-02-10\):** The signature of the `C++` function had been updated. If you still see your function signature accepts a `const char *` argument, please click the reload button to reset your code definition.

#### Solution

```python
class Solution:
    def isNumber(self, s: str) -> bool:
        try:
            float(s)
            return True
        except:
            return False
```

```python
class Solution:
    def isNumber(self, s: str) -> bool:
        s = s.strip()
        ls, pos = len(s), 0
        if ls == 0:
            return False
        if s[pos] == '+' or s[pos] == '-':
            pos += 1
        isNumeric = False
        while pos < ls and s[pos].isdigit():
            pos += 1
            isNumeric = True
        if pos < ls and s[pos] == '.':
            pos += 1
            while pos < ls and s[pos].isdigit():
                pos += 1
                isNumeric = True
        elif pos < ls and s[pos] == 'e' and isNumeric:
            isNumeric = False
            pos += 1
            if pos < ls and (s[pos] == '+' or s[pos] == '-'):
                pos += 1
            while pos < ls and s[pos].isdigit():
                pos += 1
                isNumeric = True
        print pos, ls, isNumeric
        if pos == ls and isNumeric:
            return True
        return False
```

### 136. Single Number\[E\]

[https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)

#### Description

Given a **non-empty** array of integers, every element appears _twice_ except for one. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**

```text
Input: [2,2,1]
Output: 1
```

**Example 2:**

```text
Input: [4,1,2,1,2]
Output: 4
```

#### Solution

[https://leetcode.com/problems/single-number/solution/](https://leetcode.com/problems/single-number/solution/)

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        res = 0
        for num in nums:
            res ^= num
        return res
```

### 137. Single Number II\[M\]

[https://leetcode.com/problems/single-number-ii/](https://leetcode.com/problems/single-number-ii/)

#### Description

Given a **non-empty** array of integers, every element appears _three_ times except for one, which appears exactly once. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**

```text
Input: [2,2,3,2]
Output: 3
```

**Example 2:**

```text
Input: [0,1,0,1,0,1,99]
Output: 99
```

#### Solution

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        # bitmask
        # ones as a bitmask to represent the ith bit had appeared once.
        # twos as a bitmask to represent the ith bit had appeared twice.
        # threes as a bitmask to represent the ith bit had appeared three times.
        ones, twos, threes = 0, 0, 0
        for num in nums:
            twos |= ones & num
            ones ^= num
            threes = ones & twos
            ones &= ~threes
            twos &= ~threes
        return ones
```

### 260. Single Number III\[M\]

[https://leetcode.com/problems/single-number-iii/](https://leetcode.com/problems/single-number-iii/)

#### Description

Given an array of numbers `nums`, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.

**Example:**

```text
Input:  [1,2,1,3,2,5]
Output: [3,5]
```

**Note**:

1. The order of the result is not important. So in the above example, `[5, 3]` is also correct.
2. Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?

#### Solution

```python

```

### 179. Largest Number\[M\]

[https://leetcode.com/problems/largest-number/](https://leetcode.com/problems/largest-number/)

#### Description

Given a list of non negative integers, arrange them such that they form the largest number.

**Example 1:**

```text
Input: [10,2]
Output: "210"
```

**Example 2:**

```text
Input: [3,30,34,5,9]
Output: "9534330"
```

**Note:** The result may be very large, so you need to return a string instead of an integer.

#### Solution

```python
class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        largest_num = ''.join(sorted(map(str, nums), key=LargerNumKey))
        return '0' if largest_num[0] == '0' else largest_num  
class LargerNumKey(str):
    def __lt__(x, y):
        return x + y > y + x
```

### 129. Sum Root to Leaf Numbers\[M\]

[https://leetcode.com/problems/sum-root-to-leaf-numbers/](https://leetcode.com/problems/sum-root-to-leaf-numbers/)

#### Description

Given a binary tree containing digits from `0-9` only, each root-to-leaf path could represent a number.

An example is the root-to-leaf path `1->2->3` which represents the number `123`.

Find the total sum of all root-to-leaf numbers.

**Note:** A leaf is a node with no children.

**Example:**

```text
Input: [1,2,3]
    1
   / \
  2   3
Output: 25
Explanation:
The root-to-leaf path 1->2 represents the number 12.
The root-to-leaf path 1->3 represents the number 13.
Therefore, sum = 12 + 13 = 25.
```

**Example 2:**

```text
Input: [4,9,0,5,1]
    4
   / \
  9   0
 / \
5   1
Output: 1026
Explanation:
The root-to-leaf path 4->9->5 represents the number 495.
The root-to-leaf path 4->9->1 represents the number 491.
The root-to-leaf path 4->0 represents the number 40.
Therefore, sum = 495 + 491 + 40 = 1026.
```

#### Solution

```python

```

### 200. Number of Islands\[M\]

[https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)

#### Description

Given a 2d grid map of `'1'`s \(land\) and `'0'`s \(water\), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

```text
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
```

**Example 2:**

```text
Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3
```

#### Solution

```python

```

### 202. Happy Number\[E\]

[https://leetcode.com/problems/happy-number/](https://leetcode.com/problems/happy-number/)

#### Description

Write an algorithm to determine if a number `n` is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 \(where it will stay\), or it **loops endlessly in a cycle** which does not include 1. Those numbers for which this process **ends in 1** are happy numbers.

Return True if `n` is a happy number, and False if not.

**Example:**

```text
Input: 19
Output: true
Explanation: 
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

#### Solution

[https://en.wikipedia.org/wiki/Happy\_number](https://en.wikipedia.org/wiki/Happy_number)

```python
class Solution:
    def isHappy(self, n: int) -> bool:
        seen_numbers = set()
        while n > 1 and n not in seen_numbers:
            seen_numbers.add(n)
            n = sum(map(lambda x: int(x) * int(x), list(str(n))))
        return n == 1
```

### 263. Ugly Number\[E\]

[https://leetcode.com/problems/ugly-number/](https://leetcode.com/problems/ugly-number/)

#### Description

Write a program to check whether a given number is an ugly number.

Ugly numbers are **positive numbers** whose prime factors only include `2, 3, 5`.

**Example 1:**

```text
Input: 6
Output: true
Explanation: 6 = 2 × 3
```

**Example 2:**

```text
Input: 8
Output: true
Explanation: 8 = 2 × 2 × 2
```

**Example 3:**

```text
Input: 14
Output: false 
Explanation: 14 is not ugly since it includes another prime factor 7.
```

**Note:**

1. `1` is typically treated as an ugly number.
2. Input is within the 32-bit signed integer range: \[−231, 231 − 1\].

#### Solution

```python

```

### 264. Ugly Number II\[M\]

[https://leetcode.com/problems/ugly-number-ii/](https://leetcode.com/problems/ugly-number-ii/)

#### Description

Write a program to find the `n`-th ugly number.

Ugly numbers are **positive numbers** whose prime factors only include `2, 3, 5`.

**Example:**

```text
Input: n = 10
Output: 12
Explanation: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.
```

**Note:**

1. `1` is typically treated as an ugly number.
2. `n` **does not exceed 1690**.

#### Solution

```python

```

### 268. Missing Number\[E\]

[https://leetcode.com/problems/missing-number/](https://leetcode.com/problems/missing-number/)

#### Description

Given an array containing _n_ distinct numbers taken from `0, 1, 2, ..., n`, find the one that is missing from the array.

**Example 1:**

```text
Input: [3,0,1]
Output: 2
```

**Example 2:**

```text
Input: [9,6,4,2,3,5,7,0,1]
Output: 8
```

**Note**: Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?

#### Solution

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        res = len(nums)
        for i, v in enumerate(nums):
            res ^= i
            res ^= v
        return res
```

### 374. Guess Number Higher or Lower\[E\]

[https://leetcode.com/problems/guess-number-higher-or-lower/](https://leetcode.com/problems/guess-number-higher-or-lower/)

#### Description

We are playing the Guess Game. The game is as follows:

I pick a number from **1** to _**n\**_. You have to guess which number I picked.

Every time you guess wrong, I'll tell you whether the number is higher or lower.

You call a pre-defined API `guess(int num)` which returns 3 possible results \(`-1`, `1`, or `0`\):

```text
-1 : My number is lower
 1 : My number is higher
 0 : Congrats! You got it!
```

**Example :**

```text
Input: n = 10, pick = 6
Output: 6
```

#### Solution

```python
# The guess API is already defined for you.
# @param num, your guess
# @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
# def guess(num: int) -> int:

class Solution:
    def guessNumber(self, n: int) -> int:
        begin, end = 1, n
        while begin <= end:
            mid = (begin + end) / 2
            res = guess(mid)
            if res == 0:
                return mid
            elif res > 0:
                begin = mid + 1
            else:
                end = mid - 1
```

### 375. Guess Number Higher or Lower II\[E\]

[https://leetcode.com/problems/guess-number-higher-or-lower-ii/](https://leetcode.com/problems/guess-number-higher-or-lower-ii/)

#### Description

We are playing the Guess Game. The game is as follows:

I pick a number from **1** to **n**. You have to guess which number I picked.

Every time you guess wrong, I'll tell you whether the number I picked is higher or lower.

However, when you guess a particular number x, and you guess wrong, you pay **$x**. You win the game when you guess the number I picked.

**Example:**

```text
n = 10, I pick 8.

First round:  You guess 5, I tell you that it's higher. You pay $5.
Second round: You guess 7, I tell you that it's higher. You pay $7.
Third round:  You guess 9, I tell you that it's lower. You pay $9.

Game over. 8 is the number I picked.

You end up paying $5 + $7 + $9 = $21.
```

Given a particular **n ≥ 1**, find out how much money you need to have to guarantee a **win**.

#### Solution

```python

```

### 414. Third Maximum Number\[E\]

[https://leetcode.com/problems/third-maximum-number/](https://leetcode.com/problems/third-maximum-number/)

#### Description

Given a **non-empty** array of integers, return the **third** maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O\(n\).

**Example 1:**

```text
Input: [3, 2, 1]

Output: 1

Explanation: The third maximum is 1.
```

**Example 2:**

```text
Input: [1, 2]

Output: 2

Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
```

**Example 3:**

```text
Input: [2, 2, 3, 1]

Output: 1

Explanation: Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
```

#### Solution

```python

```

### 421. Maximum XOR of Two Numbers in an Array\[M\]

[https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/)

#### Description

Given a **non-empty** array of numbers, a0, a1, a2, … , an-1, where 0 ≤ ai &lt; 231.

Find the maximum result of ai XOR aj, where 0 ≤ _i_, _j_ &lt; _n_.

Could you do this in O\(_n_\) runtime?

**Example:**

```text
Input: [3, 10, 5, 25, 2, 8]

Output: 28

Explanation: The maximum result is 5 ^ 25 = 28.
```

#### Solution

```python

```

### 434. Number of Segments in a String\[E\]

[https://leetcode.com/problems/number-of-segments-in-a-string/](https://leetcode.com/problems/number-of-segments-in-a-string/)

#### Description

Count the number of segments in a string, where a segment is defined to be a contiguous sequence of non-space characters.

Please note that the string does not contain any **non-printable** characters.

**Example:**

```text
Input: "Hello, my name is John"
Output: 5
```

#### Solution

[https://leetcode.com/problems/number-of-segments-in-a-string/solution/](https://leetcode.com/problems/number-of-segments-in-a-string/solution/)

```python
class Solution:
    def countSegments(self, s: str) -> int:
        c = 0
        for i in range(len(s)):
            if (i == 0 or s[i-1] == ' ') and s[i] != ' ':
                c += 1

        return c
```

### 448. Find All Numbers Disappeared in an Array\[E\]

[https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)

#### Description

Given an array of integers where 1 ≤ a\[i\] ≤ _n_ \(_n_ = size of array\), some elements appear twice and others appear once.

Find all the elements of \[1, _n_\] inclusive that do not appear in this array.

Could you do it without extra space and in O\(_n_\) runtime? You may assume the returned list does not count as extra space.

**Example:**

```text
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
```

#### Solution

[https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/discuss/92956/Java-accepted-simple-solution](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/discuss/92956/Java-accepted-simple-solution)

```python
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        res = []
        if nums:
            n = len(nums)
            for i in range(n):
                val = abs(nums[i]) - 1
                if nums[val] > 0:
                    nums[val] = -nums[val]
            for i in range(n):
                if nums[i] > 0:
                    res.append(i + 1)
        return res
```

### 628. Maximum Product of Three Numbers\[E\]

[https://leetcode.com/problems/maximum-product-of-three-numbers/](https://leetcode.com/problems/maximum-product-of-three-numbers/)

#### Description

Given an integer array, find three numbers whose product is maximum and output the maximum product.

**Example 1:**

```text
Input: [1,2,3]
Output: 6
```

**Example 2:**

```text
Input: [1,2,3,4]
Output: 24
```

**Note:**

1. The length of the given array will be in range \[3,104\] and all elements are in the range \[-1000, 1000\].
2. Multiplication of any three numbers in the input won't exceed the range of 32-bit signed integer.

#### Solution

[https://leetcode.com/problems/maximum-product-of-three-numbers/solution/](https://leetcode.com/problems/maximum-product-of-three-numbers/solution/)

```python
class Solution:
    def maximumProduct(self, nums: List[int]) -> int:
        min1 = min2 = float('inf')
        max1 = max2 = max3 = float('-inf')
        for num in nums:
            if num <= min1:
                min2 = min1
                min1 = num
            elif num <= min2:
                min2 = num
            if num >= max1:
                max3 = max2
                max2 = max1
                max1 = num
            elif num >= max2:
                max3 = max2
                max2 = num
            elif num >= max3:
                max3 = num
        return max(min1 * min2 * max1, max1 * max2 * max3)
```

### 933. Number of Recent Calls\[E\]

[https://leetcode.com/problems/number-of-recent-calls/](https://leetcode.com/problems/number-of-recent-calls/)

#### Description

Write a class `RecentCounter` to count recent requests.

It has only one method: `ping(int t)`, where t represents some time in milliseconds.

Return the number of `ping`s that have been made from 3000 milliseconds ago until now.

Any ping with time in `[t - 3000, t]` will count, including the current ping.

It is guaranteed that every call to `ping` uses a strictly larger value of `t` than before.

**Example 1:**

```text
Input: inputs = ["RecentCounter","ping","ping","ping","ping"], inputs = [[],[1],[100],[3001],[3002]]
Output: [null,1,2,3,3]
```

**Note:**

1. Each test case will have at most `10000` calls to `ping`.
2. Each test case will call `ping` with strictly increasing values of `t`.
3. Each call to ping will have `1 <= t <= 10^9`.

#### Solution

```python

```

