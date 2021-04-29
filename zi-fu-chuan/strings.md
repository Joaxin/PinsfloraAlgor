# Strings



### 3. Longest Substring Without Repeating Characters\[M\]

[https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

#### Description

Given a string, find the length of the **longest substring** without repeating characters.

**Example 1:**

```text
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3.
```

**Example 2:**

```text
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```text
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

#### Solution

**尝试穷举法**

```python
def lengthOfLongestSubstring(s):
    l = len(s)
    lst = {0,}
    for i in range(l):
        for j in range(i + 1 , l + 1):
            if j - i <= max(lst):
                break
            sstr = s[i:j]
            if len(set(sstr))==len(sstr):
                lst.add(len(sstr))
    return max(lst)

lengthOfLongestSubstring("pwwkew")
```

意料之中，

```text
986 / 987 test cases passed.                    Status: Time Limit Exceeded
```

优化一下，

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        l = len(s)
        ll = len(set(s))
        lst = {0,}
        lst_m = 1
        for i in range(l):
            for j in range(i + 1 + lst_m , l + 1 + ll):
                sstr = s[i:j]
                if len(set(sstr))!=len(sstr):
                    break
                else:
                    lst.add(len(sstr))
                    lst_m = len(sstr)
                    if lst_m == ll:
                        return lst_m
        return max(lst)
```

[https://leetcode.com/problems/longest-substring-without-repeating-characters/solution/](https://leetcode.com/problems/longest-substring-without-repeating-characters/solution/)

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        dicts = {}
        maxlength = start = 0
        for i,value in enumerate(s):
            if value in dicts:
                sums = dicts[value] + 1
                if sums > start:
                    start = sums
            num = i - start + 1
            if num > maxlength:
                maxlength = num
            dicts[value] = i
        return maxlength
```

[https://leetcode.com/articles/longest-substring-without-repeating-characters/](https://leetcode.com/articles/longest-substring-without-repeating-characters/)

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        charMap = {}
        for i in range(256):
            charMap[i] = -1
        ls = len(s)
        i = max_len = 0
        for j in range(ls):
            # Note that when charMap[ord(s[j])] >= i, it means that there are
            # duplicate character in current i,j. So we need to update i.
            if charMap[ord(s[j])] >= i:
                i = charMap[ord(s[j])] + 1
            charMap[ord(s[j])] = j
            max_len = max(max_len, j - i + 1)
        return max_len
```

