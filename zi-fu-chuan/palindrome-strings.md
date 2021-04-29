# Palindrome Strings

### 5. Longest Palindromic Substring\[M\]

[https://leetcode.com/problems/longest-palindromic-substring/](https://leetcode.com/problems/longest-palindromic-substring/)

#### Description

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example 1:**

```text
 Input: "babad"
 Output: "bab"
 Note: "aba" is also a valid answer.
```

**Example 2:**

```text
 Input: "cbbd"
 Output: "bb"
```

#### Solution

[https://leetcode.com/problems/longest-palindromic-substring/solution/](https://leetcode.com/problems/longest-palindromic-substring/solution/)

[有什么浅显易懂的Manacher Algorithm讲解？](https://www.zhihu.com/question/37289584)

[http://en.wikipedia.org/wiki/Longest\_palindromic\_substring](http://en.wikipedia.org/wiki/Longest_palindromic_substring)

```text
 class Solution:
     def longestPalindrome(self, s: str) -> str:
         # Transform S into T.
         # For example, S = "abba", T = "^#a#b#b#a#$".
         # ^ and $ signs are sentinels appended to each end to avoid bounds checking
         T = '#'.join('^{}$'.format(s))
         n = len(T)
         P = [0] * n
         C = R = 0
         for i in range (1, n-1):
             P[i] = (R > i) and min(R - i, P[2*C - i]) # equals to i' = C - (i-C)
             # Attempt to expand palindrome centered at i
             while T[i + 1 + P[i]] == T[i - 1 - P[i]]:
                 P[i] += 1
     
             # If palindrome centered at i expand past R,
             # adjust center based on expanded palindrome.
             if i + P[i] > R:
                 C, R = i, i + P[i]
     
         # Find the maximum element in P.
         maxLen, centerIndex = max((n, i) for i, n in enumerate(P))
         return s[(centerIndex - maxLen)//2: (centerIndex + maxLen)//2]
```

### 214. Shortest Palindrome\[H\]

[https://leetcode.com/problems/shortest-palindrome/](https://leetcode.com/problems/shortest-palindrome/)

#### Description

Given a string _**s**_, you are allowed to convert it to a palindrome by adding characters in front of it. Find and return the shortest palindrome you can find by performing this transformation.

**Example 1:**

```text
 Input: "aacecaaa"
 Output: "aaacecaaa"
```

**Example 2:**

```text
 Input: "abcd"
 Output: "dcbabcd"
```

#### Solution

[https://leetcode.com/problems/shortest-palindrome/solution/](https://leetcode.com/problems/shortest-palindrome/solution/)

[https://leetcode.com/problems/shortest-palindrome/discuss/60250/My-recursive-Python-solution](https://leetcode.com/problems/shortest-palindrome/discuss/60250/My-recursive-Python-solution)

```text
 class Solution:
     def shortestPalindrome(self, s: str) -> str:
         if not s or len(s) == 1:
             return s
         j = 0
         for i in reversed(range(len(s))):
             if s[i] == s[j]:
                 j += 1
         return s[::-1][:len(s)-j] + self.shortestPalindrome(s[:j-len(s)]) + s[j-len(s):]
```

