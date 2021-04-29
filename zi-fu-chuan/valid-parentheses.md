# Valid Parentheses



## 20. Valid Parentheses\[E\]

[https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)

#### Description

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

**Example 1:**

```text
Input: "()"
Output: true
```

**Example 2:**

```text
Input: "()[]{}"
Output: true
```

**Example 3:**

```text
Input: "(]"
Output: false
```

**Example 4:**

```text
Input: "([)]"
Output: false
```

**Example 5:**

```text
Input: "{[]}"
Output: true
```

#### Solution

```python
class Solution:
    def isValid(self, s: str) -> bool:
        brackets = ["()", "[]", "{}"]
        while any(bra in s for bra in brackets):
            for bracket in brackets:
                s = s.replace(bracket,'')
        return not s
```

[https://leetcode.com/problems/valid-parentheses/solution/](https://leetcode.com/problems/valid-parentheses/solution/)

```python
def isValid(self, s):
    bracket_map = {"(": ")", "[": "]",  "{": "}"}
    open_par = set(["(", "[", "{"])
    stack = []
    for i in s:
        if i in open_par:
            stack.append(i)
        elif stack and i == bracket_map[stack[-1]]:
                stack.pop()
        else:
            return False
    return stack == []
```

### 32. Longest Valid Parentheses\[H\]

[https://leetcode.com/problems/longest-valid-parentheses/](https://leetcode.com/problems/longest-valid-parentheses/)

#### Description

Given a string containing just the characters `'('` and `')'`, find the length of the longest valid \(well-formed\) parentheses substring.

**Example 1:**

```text
Input: "(()"
Output: 2
Explanation: The longest valid parentheses substring is "()"
```

**Example 2:**

```text
Input: ")()())"
Output: 4
Explanation: The longest valid parentheses substring is "()()"
```

#### Solution

[https://leetcode.com/problems/longest-valid-parentheses/solution/](https://leetcode.com/problems/longest-valid-parentheses/solution/)

```python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        ls = len(s)
        stack = []
        data = [0] * ls
        for i in range(ls):
            curr = s[i]
            if curr == '(':
                stack.append(i)
            else:
                if len(stack) > 0:
                    data[i] = 1
                    data[stack.pop(-1)] = 1
        tep, res = 0, 0
        for t in data:
            if t == 1:
                tep += 1
            else:
                res = max(tep, res)
                tep = 0
        return max(tep, res)
```

### 301. Remove Invalid Parentheses\[H\]

[https://leetcode.com/problems/remove-invalid-parentheses/](https://leetcode.com/problems/remove-invalid-parentheses/)

#### Description

Remove the minimum number of invalid parentheses in order to make the input string valid. Return all possible results.

**Note:** The input string may contain letters other than the parentheses `(` and `)`.

**Example 1:**

```text
Input: "()())()"
Output: ["()()()", "(())()"]
```

**Example 2:**

```text
Input: "(a)())()"
Output: ["(a)()()", "(a())()"]
```

**Example 3:**

```text
Input: ")("
Output: [""]
```

#### Solution

[https://leetcode.com/problems/remove-invalid-parentheses/solution/](https://leetcode.com/problems/remove-invalid-parentheses/solution/)

[https://leetcode.com/problems/remove-invalid-parentheses/discuss/75028/Short-Python-BFS](https://leetcode.com/problems/remove-invalid-parentheses/discuss/75028/Short-Python-BFS)

```python

```

### 22. Generate Parentheses

[https://leetcode.com/problems/generate-parentheses/](https://leetcode.com/problems/generate-parentheses/)

#### Description

Given _n_ pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given _n_ = 3, a solution set is:

```text
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```

#### Solution

[https://leetcode.com/problems/generate-parentheses/solution/](https://leetcode.com/problems/generate-parentheses/solution/)

```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        if n == 1:
            return ['()']
        llist = self.generateParenthesis(n - 1)
        res = []
        for l in llist:
            curr = l + ')'
            for index in range(len(curr)):
                if curr[index] == ')':
                    res.append(curr[:index] + '(' + curr[index:])
        return list(set(res))
```

