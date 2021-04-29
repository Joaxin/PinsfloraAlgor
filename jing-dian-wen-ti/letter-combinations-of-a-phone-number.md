# Letter Combinations of a Phone Number



### 17. Letter Combinations of a Phone Number\[M\]

[https://leetcode.com/problems/letter-combinations-of-a-phone-number/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

#### Description

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters \(just like on the telephone buttons\) is given below. Note that 1 does not map to any letters.

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

**Example:**

```text
Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

**Note:**

Although the above answer is in lexicographical order, your answer could be in any order you want.

#### Solution

```python
class Solution:
    def __init__(self):
        self.map = {'1':"", '2':"abc", '3':"def", '4':"ghi", '5':"jkl", 
                    '6':"mno", '7':"pqrs", '8':"tuv", '9':"wxyz"}
        self.res = []
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits:
            return None
        tmp = ""
        self.combo(digits, tmp)
        return self.res

    def combo(self, digits, tmp):
        if not digits:
            self.res.append(tmp)
        else:
            for ch in self.map[digits[0]]:
                self.combo(digits[1:],tmp + ch)
```

