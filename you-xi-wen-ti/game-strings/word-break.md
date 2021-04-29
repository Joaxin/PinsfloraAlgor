# Word Break



### 139. Word Break\[M\]

[https://leetcode.com/problems/word-break/](https://leetcode.com/problems/word-break/)

#### Description

Given a **non-empty** string _s_ and a dictionary _wordDict_ containing a list of **non-empty** words, determine if _s_ can be segmented into a space-separated sequence of one or more dictionary words.

**Note:**

* The same word in the dictionary may be reused multiple times in the segmentation.
* You may assume the dictionary does not contain duplicate words.

**Example 1:**

```text
Input: s = "leetcode", wordDict = ["leet", "code"]
Output: true
Explanation: Return true because "leetcode" can be segmented as "leet code".
```

**Example 2:**

```text
Input: s = "applepenapple", wordDict = ["apple", "pen"]
Output: true
Explanation: Return true because "applepenapple" can be segmented as "apple pen apple".
             Note that you are allowed to reuse a dictionary word.
```

**Example 3:**

```text
Input: s = "catsandog", wordDict = ["cats", "dog", "sand", "and", "cat"]
Output: false
```

#### Solution

```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        queue = [0]
        ls = len(s)
        lenList = [l for l in set(map(len, wordDict))]
        visited = [0 for _ in range(0, ls + 1)]
        while queue:
            start = queue.pop(0)
            for l in lenList:
                if s[start:start + l] in wordDict:
                    if start + l == ls:
                        return True
                    if visited[start + l] == 0:
                        queue.append(start + l)
                        visited[start + l] = 1
        return False
```

### 140. Word Break II\[H\]

[https://leetcode.com/problems/word-break-ii/](https://leetcode.com/problems/word-break-ii/)

#### Description

Given a **non-empty** string _s_ and a dictionary _wordDict_ containing a list of **non-empty** words, add spaces in _s_ to construct a sentence where each word is a valid dictionary word. Return all such possible sentences.

**Note:**

* The same word in the dictionary may be reused multiple times in the segmentation.
* You may assume the dictionary does not contain duplicate words.

**Example 1:**

```text
Input:
s = "catsanddog"
wordDict = ["cat", "cats", "and", "sand", "dog"]
Output:
[
  "cats and dog",
  "cat sand dog"
]
```

**Example 2:**

```text
Input:
s = "pineapplepenapple"
wordDict = ["apple", "pen", "applepen", "pine", "pineapple"]
Output:
[
  "pine apple pen apple",
  "pineapple pen apple",
  "pine applepen apple"
]
Explanation: Note that you are allowed to reuse a dictionary word.
```

**Example 3:**

```text
Input:
s = "catsandog"
wordDict = ["cats", "dog", "sand", "and", "cat"]
Output:
[]
```

#### Solution

[https://discuss.leetcode.com/topic/12997/11ms-c-solution-concise](https://discuss.leetcode.com/topic/12997/11ms-c-solution-concise)

```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> List[str]:
        solution = {}
        try:
            return solution[s]
        except KeyError:
            pass
        result = []
        if s in wordDict:
            result.append(s)
        for i in range(1, len(s)):
            word = s[i:]
            if word in wordDict:
                rem = s[:i]
                prev = self.wordBreak(rem, wordDict)
                result.extend([res + ' ' + word for res in prev])
        solution[s] = result
        return result
```

