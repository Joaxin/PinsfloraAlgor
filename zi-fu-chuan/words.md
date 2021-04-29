# Words



### 58. Length of Last Word\[E\]

[https://leetcode.com/problems/length-of-last-word/](https://leetcode.com/problems/length-of-last-word/)

#### Description

Given a string _s_ consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word \(last word means the last appearing word if we loop from left to right\) in the string.

If the last word does not exist, return 0.

**Note:** A word is defined as a **maximal substring** consisting of non-space characters only.

**Example:**

```text
Input: "Hello World"
Output: 5
```

#### Solution

```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        return len(s.rstrip().split(" ")[-1])
```

```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        ss = s.rstrip().split(" ")
        return len(ss[len(ss)-1])
```

### 68. Text Justification\[H\]

[https://leetcode.com/problems/text-justification/](https://leetcode.com/problems/text-justification/)

#### Description

Given an array of words and a width _maxWidth_, format the text such that each line has exactly _maxWidth_ characters and is fully \(left and right\) justified.

You should pack your words in a greedy approach; that is, pack as many words as you can in each line. Pad extra spaces `' '` when necessary so that each line has exactly _maxWidth_ characters.

Extra spaces between words should be distributed as evenly as possible. If the number of spaces on a line do not divide evenly between words, the empty slots on the left will be assigned more spaces than the slots on the right.

For the last line of text, it should be left justified and no **extra** space is inserted between words.

**Note:**

* A word is defined as a character sequence consisting of non-space characters only.
* Each word's length is guaranteed to be greater than 0 and not exceed _maxWidth_.
* The input array `words` contains at least one word.

**Example 1:**

```text
Input:
words = ["This", "is", "an", "example", "of", "text", "justification."]
maxWidth = 16
Output:
[
   "This    is    an",
   "example  of text",
   "justification.  "
]
```

**Example 2:**

```text
Input:
words = ["What","must","be","acknowledgment","shall","be"]
maxWidth = 16
Output:
[
  "What   must   be",
  "acknowledgment  ",
  "shall be        "
]
Explanation: Note that the last line is "shall be    " instead of "shall     be",
             because the last line must be left-justified instead of fully-justified.
             Note that the second line is also left-justified becase it contains only one word.
```

**Example 3:**

```text
Input:
words = ["Science","is","what","we","understand","well","enough","to","explain",
         "to","a","computer.","Art","is","everything","else","we","do"]
maxWidth = 20
Output:
[
  "Science  is  what we",
  "understand      well",
  "enough to explain to",
  "a  computer.  Art is",
  "everything  else  we",
  "do                  "
]
```

#### Solution

```python

```

### 79. Word Search\[M\]

[https://leetcode.com/problems/word-search/](https://leetcode.com/problems/word-search/)

#### Description

Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

**Example:**

```text
board =
[
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]

Given word = "ABCCED", return true.
Given word = "SEE", return true.
Given word = "ABCB", return false.
```

**Constraints:**

* `board` and `word` consists only of lowercase and uppercase English letters.
* `1 <= board.length <= 200`
* `1 <= board[i].length <= 200`
* `1 <= word.length <= 10^3`

#### Solution

```python

```

### 126. Word Ladder II\[H\]

[https://leetcode.com/problems/word-ladder-ii/](https://leetcode.com/problems/word-ladder-ii/)

#### Description

Given two words \(_beginWord_ and _endWord_\), and a dictionary's word list, find all shortest transformation sequence\(s\) from _beginWord_ to _endWord_, such that:

1. Only one letter can be changed at a time
2. Each transformed word must exist in the word list. Note that _beginWord_ is _not_ a transformed word.

**Note:**

* Return an empty list if there is no such transformation sequence.
* All words have the same length.
* All words contain only lowercase alphabetic characters.
* You may assume no duplicates in the word list.
* You may assume _beginWord_ and _endWord_ are non-empty and are not the same.

**Example 1:**

```text
Input:
beginWord = "hit",
endWord = "cog",
wordList = ["hot","dot","dog","lot","log","cog"]

Output:
[
  ["hit","hot","dot","dog","cog"],
  ["hit","hot","lot","log","cog"]
]
```

**Example 2:**

```text
Input:
beginWord = "hit"
endWord = "cog"
wordList = ["hot","dot","dog","lot","log"]

Output: []

Explanation: The endWord "cog" is not in wordList, therefore no possible transformation.
```

#### Solution

```python

```

### 127. Word Ladder\[M\]

[https://leetcode.com/problems/word-ladder/](https://leetcode.com/problems/word-ladder/)

#### Description

Given two words \(_beginWord_ and _endWord_\), and a dictionary's word list, find the length of shortest transformation sequence from _beginWord_ to _endWord_, such that:

1. Only one letter can be changed at a time.
2. Each transformed word must exist in the word list.

**Note:**

* Return 0 if there is no such transformation sequence.
* All words have the same length.
* All words contain only lowercase alphabetic characters.
* You may assume no duplicates in the word list.
* You may assume _beginWord_ and _endWord_ are non-empty and are not the same.

**Example 1:**

```text
Input:
beginWord = "hit",
endWord = "cog",
wordList = ["hot","dot","dog","lot","log","cog"]

Output: 5

Explanation: As one shortest transformation is "hit" -> "hot" -> "dot" -> "dog" -> "cog",
return its length 5.
```

**Example 2:**

```text
Input:
beginWord = "hit"
endWord = "cog"
wordList = ["hot","dot","dog","lot","log"]

Output: 0

Explanation: The endWord "cog" is not in wordList, therefore no possible transformation.
```

#### Solution

```python

```

### 290. Word Pattern\[E\]

[https://leetcode.com/problems/word-pattern/](https://leetcode.com/problems/word-pattern/)

#### Description

Given a `pattern` and a string `str`, find if `str` follows the same pattern.

Here **follow** means a full match, such that there is a bijection between a letter in `pattern` and a **non-empty** word in `str`.

**Example 1:**

```text
Input: pattern = "abba", str = "dog cat cat dog"
Output: true
```

**Example 2:**

```text
Input:pattern = "abba", str = "dog cat cat fish"
Output: false
```

**Example 3:**

```text
Input: pattern = "aaaa", str = "dog cat cat dog"
Output: false
```

**Example 4:**

```text
Input: pattern = "abba", str = "dog dog dog dog"
Output: false
```

**Notes:** You may assume `pattern` contains only lowercase letters, and `str` contains lowercase letters that may be separated by a single space.

#### Solution

```python

```

### 151. Reverse Words in a String\[M\]

[https://leetcode.com/problems/reverse-words-in-a-string/](https://leetcode.com/problems/reverse-words-in-a-string/)

#### Description

Given an input string, reverse the string word by word.

**Example 1:**

```text
Input: "the sky is blue"
Output: "blue is sky the"
```

**Example 2:**

```text
Input: "  hello world!  "
Output: "world! hello"
Explanation: Your reversed string should not contain leading or trailing spaces.
```

**Example 3:**

```text
Input: "a good   example"
Output: "example good a"
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.
```

**Note:**

* A word is defined as a sequence of non-space characters.
* Input string may contain leading or trailing spaces. However, your reversed string should not contain leading or trailing spaces.
* You need to reduce multiple spaces between two words to a single space in the reversed string.

**Follow up:**

For C programmers, try to solve it _in-place_ in _O_\(1\) extra space.

#### Solution

```python

```

### 442. Find All Duplicates in an Array\[M\]

[https://leetcode.com/problems/find-all-duplicates-in-an-array/](https://leetcode.com/problems/find-all-duplicates-in-an-array/)

#### Description

Given an array of integers, 1 ≤ a\[i\] ≤ _n_ \(_n_ = size of array\), some elements appear **twice** and others appear **once**.

Find all the elements that appear **twice** in this array.

Could you do it without extra space and in O\(_n_\) runtime?

**Example:**

```text
Input:
[4,3,2,7,8,2,3,1]

Output:
[2,3]
```

#### Solution

```python

```

### 692. Top K Frequent Words\[M\]

[https://leetcode.com/problems/top-k-frequent-words/](https://leetcode.com/problems/top-k-frequent-words/)

#### Description

Given a non-empty list of words, return the _k_ most frequent elements.

Your answer should be sorted by frequency from highest to lowest. If two words have the same frequency, then the word with the lower alphabetical order comes first.

**Example 1:**

```text
Input: ["i", "love", "leetcode", "i", "love", "coding"], k = 2
Output: ["i", "love"]
Explanation: "i" and "love" are the two most frequent words.
    Note that "i" comes before "love" due to a lower alphabetical order.
```

**Example 2:**

```text
Input: ["the", "day", "is", "sunny", "the", "the", "the", "sunny", "is", "is"], k = 4
Output: ["the", "is", "sunny", "day"]
Explanation: "the", "is", "sunny" and "day" are the four most frequent words,
    with the number of occurrence being 4, 3, 2 and 1 respectively.
```

**Note:**

1. You may assume _k_ is always valid, 1 ≤ _k_ ≤ number of unique elements.
2. Input words contain only lowercase letters.

**Follow up:**

1. Try to solve it in _O_\(_n_ log _k_\) time and _O_\(_n_\) extra space.

#### Solution

```python

```

### 720. Longest Word in Dictionary\[E\]

[https://leetcode.com/problems/longest-word-in-dictionary/](https://leetcode.com/problems/longest-word-in-dictionary/)

#### Description

Given a list of strings `words` representing an English Dictionary, find the longest word in `words` that can be built one character at a time by other words in `words`. If there is more than one possible answer, return the longest word with the smallest lexicographical order.

If there is no answer, return the empty string.

**Example 1:**

```text
Input: 
words = ["w","wo","wor","worl", "world"]
Output: "world"
Explanation: 
The word "world" can be built one character at a time by "w", "wo", "wor", and "worl".
```

**Example 2:**

```text
Input: 
words = ["a", "banana", "app", "appl", "ap", "apply", "apple"]
Output: "apple"
Explanation: 
Both "apply" and "apple" can be built from other words in the dictionary. However, "apple" is lexicographically smaller than "apply".
```

**Note:**

All the strings in the input will only contain lowercase letters.

The length of `words` will be in the range `[1, 1000]`.

The length of `words[i]` will be in the range `[1, 30]`.

#### Solution

```python

```

### 819. Most Common Word\[E\]

[https://leetcode.com/problems/most-common-word/](https://leetcode.com/problems/most-common-word/)

#### Description

Given a paragraph and a list of banned words, return the most frequent word that is not in the list of banned words. It is guaranteed there is at least one word that isn't banned, and that the answer is unique.

Words in the list of banned words are given in lowercase, and free of punctuation. Words in the paragraph are not case sensitive. The answer is in lowercase.

**Example:**

```text
Input: 
paragraph = "Bob hit a ball, the hit BALL flew far after it was hit."
banned = ["hit"]
Output: "ball"
Explanation: 
"hit" occurs 3 times, but it is a banned word.
"ball" occurs twice (and no other word does), so it is the most frequent non-banned word in the paragraph. 
Note that words in the paragraph are not case sensitive,
that punctuation is ignored (even if adjacent to words, such as "ball,"), 
and that "hit" isn't the answer even though it occurs more because it is banned.
```

**Note:**

* `1 <= paragraph.length <= 1000`.
* `0 <= banned.length <= 100`.
* `1 <= banned[i].length <= 10`.
* The answer is unique, and written in lowercase \(even if its occurrences in `paragraph` may have uppercase symbols, and even if it is a proper noun.\)
* `paragraph` only consists of letters, spaces, or the punctuation symbols `!?',;.`
* There are no hyphens or hyphenated words.
* Words only consist of letters, never apostrophes or other punctuation symbols.

#### Solution

```python

```

