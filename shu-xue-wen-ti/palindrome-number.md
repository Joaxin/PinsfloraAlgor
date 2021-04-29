# Palindrome Number

### 9.Palindrome Number

[https://leetcode.com/problems/palindrome-number/](https://leetcode.com/problems/palindrome-number/)

#### Description

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

**Example 1:**

```text
 Input: 121
 Output: true
```

**Example 2:**

```text
 Input: -121
 Output: false
 Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

**Example 3:**

```text
 Input: 10
 Output: false
 Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

**Follow up:**

Coud you solve it without converting the integer to a string?

#### Solution

```text
 class Solution(object):
     def isPalindrome(self, x):
 ​
         nx = x
         if nx < 0:
             return False
         num = 0
         while nx > 0:
             num *= 10
             num += nx % 10
             nx //= 10
         return num == x
```

### 125. Valid Palindrome

[https://leetcode.com/problems/valid-palindrome/](https://leetcode.com/problems/valid-palindrome/)

#### Description

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

**Note:** For the purpose of this problem, we define empty string as valid palindrome.

**Example 1:**

```text
 Input: "A man, a plan, a canal: Panama"
 Output: true
```

**Example 2:**

```text
 Input: "race a car"
 Output: false
```

**Constraints:**

* `s` consists only of printable ASCII characters.

#### Solution

```text
 class Solution:
     def isPalindrome(self, s: str) -> bool:
         s = "".join(i for i in s.upper() if i.isalnum())
         return s == s[::-1]
```

不用`s == s[::-1]`的代码：

```text
 class Solution(object):
     def isPalindrome(self, s):
         """
         :type s: str
         :rtype: bool
         """
         s = "".join(i for i in s.upper() if i.isalnum())
         ls = len(s)
         if ls <= 1:
             return True
         mid = ls / 2
         for i in range(mid):
             if s[i] != s[ls - 1 - i]:
                 return False
         return True
```

### 131. Palindrome Partitioning

[https://leetcode.com/problems/palindrome-partitioning/](https://leetcode.com/problems/palindrome-partitioning/)

#### Description

Given a string _s_, partition _s_ such that every substring of the partition is a palindrome.

Return all possible palindrome partitioning of _s_.

**Example:**

```text
 Input: "aab"
 Output:
 [
   ["aa","b"],
   ["a","a","b"]
 ]
```

#### Solution

```text
 ​
 def partition(s):
         def isPalindrome(begin, end):
             while begin < end:
                 if s[begin] != s[end]:
                     return False
                 begin += 1
                 end -= 1
             return True
 ​
         res = []
         def make(begin, lst):
             if begin == len(s):
                 res.append(lst)
             else:
                 for i in range(begin, len(s)):
                     if (isPalindrome(begin,i)):
                         nlst = lst[:]
                         nlst.append(s[begin:i+1])
                         make(i + 1, nlst)
         make(0,[])
         
         return res
 print(partition("aab"))
```

### 132. Palindrome Partitioning II\[H\]

[https://leetcode.com/problems/palindrome-partitioning-ii/](https://leetcode.com/problems/palindrome-partitioning-ii/)

#### Description

Given a string _s_, partition _s_ such that every substring of the partition is a palindrome.

Return the minimum cuts needed for a palindrome partitioning of _s_.

**Example:**

```text
 Input: "aab"
 Output: 1
 Explanation: The palindrome partitioning ["aa","b"] could be produced using 1 cut.
```

#### Solution

[https://leetcode.com/problems/palindrome-partitioning-ii/discuss/42198/my-solution-does-not-need-a-table-for-palindrome-is-it-right-it-uses-only-on-space](https://leetcode.com/problems/palindrome-partitioning-ii/discuss/42198/my-solution-does-not-need-a-table-for-palindrome-is-it-right-it-uses-only-on-space)

```text
 class Solution:
     def minCut(self, s: str) -> int:
         size = len(s)
         cut = list(range(-1, size))
         for idx in range(1, size):
             for low, high in (idx, idx), (idx - 1, idx):
                 while low >= 0 and high < size and s[low] == s[high]:
                     cut[high + 1] = min(cut[high + 1], cut[low] + 1)
                     low -= 1
                     high += 1
         return cut[-1]
```

### 234. Palindrome Linked List

[https://leetcode.com/problems/palindrome-linked-list/](https://leetcode.com/problems/palindrome-linked-list/)

#### Description

Given a singly linked list, determine if it is a palindrome.

**Example 1:**

```text
 Input: 1->2
 Output: false
```

**Example 2:**

```text
 Input: 1->2->2->1
 Output: true
```

**Follow up:** Could you do it in O\(n\) time and O\(1\) space?

#### Solution

```text
 # Definition for singly-linked list.
 # class ListNode:
 #     def __init__(self, val=0, next=None):
 #         self.val = val
 #         self.next = next
 class Solution:
     def isPalindrome(self, head: ListNode) -> bool:
         curr = head
         lst = []
         while curr:
             lst.append(curr.val)
             curr = curr.next
         return lst == lst[::-1]
```

### 336. Palindrome Linked List\[H\]

[https://leetcode.com/problems/palindrome-pairs/](https://leetcode.com/problems/palindrome-pairs/)

#### Description

Given a list of **unique** words, find all pairs of **\*distinct\*** indices `(i, j)` in the given list, so that the concatenation of the two words, i.e. `words[i] + words[j]` is a palindrome.

**Example 1:**

```text
 Input: ["abcd","dcba","lls","s","sssll"]
 Output: [[0,1],[1,0],[3,2],[2,4]] 
 Explanation: The palindromes are ["dcbaabcd","abcddcba","slls","llssssll"]
```

**Example 2:**

```text
 Input: ["bat","tab","cat"]
 Output: [[0,1],[1,0]] 
 Explanation: The palindromes are ["battab","tabbat"]
```

#### Solution

[https://leetcode.com/problems/palindrome-pairs/discuss/79219/Python-solution](https://leetcode.com/problems/palindrome-pairs/discuss/79219/Python-solution)~

```text
 class Solution:
     def palindromePairs(self, words: List[str]) -> List[List[int]]:
         # reverse word and create a word to index map
         idx, res = dict([(w[::-1], i) for i, w in enumerate(words)]), []
         for i, word in enumerate(words):
             for j in range(len(word) + 1):
                 # Use prefix and postfix
                 # rather than going through all posible combinations
                 pre, post = word[:j], word[j:]
                 if pre in idx and i != idx[pre] and post == post[::-1]:
                     res.append([i, idx[pre]])
                 # reverse(post) + pre + post
                 if j > 0 and post in idx and i != idx[post] and pre == pre[::-1]:
                     res.append([idx[post], i])
         return res
```

### 409. Longest Palindrome

[https://leetcode.com/problems/longest-palindrome/](https://leetcode.com/problems/longest-palindrome/)

#### Description

Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example `"Aa"` is not considered a palindrome here.

**Note:** Assume the length of given string will not exceed 1,010.

**Example:**

```text
 Input:
 "abccccdd"
 ​
 Output:
 7
 ​
 Explanation:
 One longest palindrome that can be built is "dccaccd", whose length is 7.
```

#### Solution

[https://leetcode.com/problems/longest-palindrome/solution/](https://leetcode.com/problems/longest-palindrome/solution/)

```text
 def longestPalindrome(self, s):
     ans = 0
     for v in collections.Counter(s).values():
         ans += v // 2 * 2
         if ans % 2 == 0 and v % 2 == 1:
             ans += 1
     return ans
```

### 479. Largest Palindrome Product\[H\]

[https://leetcode.com/problems/largest-palindrome-product/](https://leetcode.com/problems/largest-palindrome-product/)

#### Description

Find the largest palindrome made from the product of two n-digit numbers.

Since the result could be very large, you should return the largest palindrome mod 1337.

**Example:**

Input: 2

Output: 987

Explanation: 99 x 91 = 9009, 9009 % 1337 = 987

**Note:**

The range of n is \[1,8\].

#### Solution

[https://leetcode.com/problems/largest-palindrome-product/discuss/96305/Python-Solution-Using-Math-In-48ms](https://leetcode.com/problems/largest-palindrome-product/discuss/96305/Python-Solution-Using-Math-In-48ms) [https://leetcode.com/problems/largest-palindrome-product/discuss/96294/could-any-python-experts-share-their-codes-within-100ms](https://leetcode.com/problems/largest-palindrome-product/discuss/96294/could-any-python-experts-share-their-codes-within-100ms)

```text
 class Solution:
     def largestPalindrome(self, n):
         if n == 1:
             return 9
         for a in range(2, 9 * 10 ** (n - 1)):
             hi = (10 ** n) - a
             lo = int(str(hi)[::-1])
             if a ** 2 - 4 * lo < 0:
                 continue
             if (a ** 2 - 4 * lo) ** .5 == int((a ** 2 - 4 * lo) ** .5):
                 return (lo + 10 ** n * (10 ** n - a)) % 1337
```

### 680. Valid Palindrome II

[https://leetcode.com/problems/valid-palindrome-ii/](https://leetcode.com/problems/valid-palindrome-ii/)

#### Description

Given a non-empty string `s`, you may delete **at most** one character. Judge whether you can make it a palindrome.

**Example 1:**

```text
 Input: "aba"
 Output: True
```

**Example 2:**

```text
 Input: "abca"
 Output: True
 Explanation: You could delete the character 'c'.
```

**Note:**

1. The string will only contain lowercase characters a-z. The maximum length of the string is 50000.

#### Solution

[https://leetcode.com/problems/valid-palindrome-ii/solution/](https://leetcode.com/problems/valid-palindrome-ii/solution/)

[https://leetcode.com/problems/valid-palindrome-ii/discuss/701203/Python-Concise-O\(n\)](https://leetcode.com/problems/valid-palindrome-ii/discuss/701203/Python-Concise-O%28n%29)

```text
 class Solution:
     def validPalindrome(self, s: str) -> bool:
         l, r = 0, len(s)-1
         while l < r:
             if s[l] == s[r]:
                 l += 1
                 r -= 1
             else:
                 break
         return s[l:r] == s[l:r][::-1] or s[l+1:r+1] == s[l+1:r+1][::-1]
```

