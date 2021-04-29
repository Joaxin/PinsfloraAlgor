# Minimum Window Substring



### 482. License Key Formatting\[E\]

[https://leetcode.com/problems/license-key-formatting/](https://leetcode.com/problems/license-key-formatting/)

#### Description

You are given a license key represented as a string S which consists only alphanumeric character and dashes. The string is separated into N+1 groups by N dashes.

Given a number K, we would want to reformat the strings such that each group contains _exactly_ K characters, except for the first group which could be shorter than K, but still must contain at least one character. Furthermore, there must be a dash inserted between two groups and all lowercase letters should be converted to uppercase.

Given a non-empty string S and a number K, format the string according to the rules described above.

**Example 1:**

```text
Input: S = "5F3Z-2e-9-w", K = 4

Output: "5F3Z-2E9W"

Explanation: The string S has been split into two parts, each part has 4 characters.
Note that the two extra dashes are not needed and can be removed.
```

**Example 2:**

```text
Input: S = "2-5g-3-J", K = 2

Output: "2-5G-3J"

Explanation: The string S has been split into three parts, each part has 2 characters except the first part as it could be shorter as mentioned above.
```

**Note:**

1. The length of string S will not exceed 12,000, and K is a positive integer.
2. String S consists only of alphanumerical characters \(a-z and/or A-Z and/or 0-9\) and dashes\(-\).
3. String S is non-empty.

#### Solution

**Slow**

```python
class Solution:
    def licenseKeyFormatting(self, S: str, K: int) -> str:
        S = S.replace("-","").upper()
        res = list(S)
        l = len(S)
        for i in range(l, 0, -K):
            if l - K > 0 and i != l:
                res.insert(i ,"-")
        return "".join(res)
```

[https://leetcode.com/problems/license-key-formatting/discuss/96497/Python-solution](https://leetcode.com/problems/license-key-formatting/discuss/96497/Python-solution)

```python
class Solution:
    def licenseKeyFormatting(self, S: str, K: int) -> str:
        S = S.upper().replace('-', '')
        ls = len(S)
        if ls % K == 0:
            pos = K
        else:
            pos = ls % K
        res = S[:pos]
        while pos < ls:
            res += '-' + S[pos:pos + K]
            pos += K
        return res
```

