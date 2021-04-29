# Substring



### 30. Substring with Concatenation of All Words\[H\]

[https://leetcode.com/problems/substring-with-concatenation-of-all-words/](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)

#### Description

ng\(s\) in **s** that is a concatenation of each word in **words** exactly once and without any intervening characters.

**Example 1:**

```text
Input:
  s = "barfoothefoobarman",
  words = ["foo","bar"]
Output: [0,9]
Explanation: Substrings starting at index 0 and 9 are "barfoo" and "foobar" respectively.
The output order does not matter, returning [9,0] is fine too.
```

**Example 2:**

```text
Input:
  s = "wordgoodgoodgoodbestword",
  words = ["word","good","best","word"]
Output: []
```

#### Solution

```python
class Solution:
    def findSubstring(self, s: str, words: List[str]) -> List[int]:
        ls = len(s)
        word_ls = len(words[0])
        target_dict = {}
        # create a targe dict for match
        for word in words:
            try:
                target_dict[word] += 1
            except KeyError:
                target_dict[word] = 1
        res = []
        for start in range(ls - word_ls * len(words) + 1):
            curr_dict = target_dict.copy()
            for pos in range(start, start + word_ls * len(words), word_ls):
                curr = s[pos:pos + word_ls]
                try:
                    curr_dict[curr] -= 1
                    # word appears more than target
                    if curr_dict[curr] < 0:
                        break
                except KeyError:
                    # word not in words
                    break
            else:
                # all word in target dict
                res.append(start)
        return res
```

[https://leetcode.com/discuss/87745/3-line-python-solution-sorted-hash-112ms](https://leetcode.com/discuss/87745/3-line-python-solution-sorted-hash-112ms)

```python
    def findSubstring(self, s, words):
        wLen, wtLen, wSet, sortHash, sLen = len(words[0]), len(words[0]) * len(words), set(words), sorted(
            [hash(w) for w in words]), len(s)
        h = [hash(s[i:i + wLen]) if s[i:i + wLen] in wSet else None for i in xrange(sLen - wLen + 1)]
        return [i for i in xrange(sLen - wtLen + 1) if h[i] and sorted(h[i: i + wtLen: wLen]) == sortHash]
```

### 395. Longest Substring with At Least K Repeating Characters\[M\]

[https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/)

#### Description

Find the length of the longest substring _**T\**_ of a given string \(consists of lowercase letters only\) such that every character in _**T\**_ appears no less than _k_ times.

**Example 1:**

```text
Input:
s = "aaabb", k = 3

Output:
3

The longest substring is "aaa", as 'a' is repeated 3 times.
```

**Example 2:**

```text
Input:
s = "ababbc", k = 2

Output:
5

The longest substring is "ababb", as 'a' is repeated 2 times and 'b' is repeated 3 times.
```

#### Solution

```python

```

