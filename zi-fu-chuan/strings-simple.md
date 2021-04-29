# Strings Simple



### 14. Longest Common Prefix

[https://leetcode.com/problems/implement-strstr/](https://leetcode.com/problems/implement-strstr/)

#### Description

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

**Example 1:**

```text
Input: ["flower","flow","flight"]
Output: "fl"
```

**Example 2:**

```text
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Note:**

All given inputs are in lowercase letters `a-z`.

#### Solution

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        prefix = []
        num = len(strs)
        for x in zip(*strs):
            if len(set(x)) == 1:
                prefix.append(x[0])
            else:
                break
        return "".join(prefix)
```

[https://leetcode.com/discuss/89987/one-line-solution-using-itertools-takewhile](https://leetcode.com/discuss/89987/one-line-solution-using-itertools-takewhile)

```python
def longestCommonPrefix(self, strs):
    return reduce(lambda s1, s2: ''.join(y[0] for y in itertools.takewhile(lambda x: x[0] == x[1], zip(s1, s2))), strs or [''])
```

### 28. Implement strStr\(\)

[https://leetcode.com/problems/implement-strstr/](https://leetcode.com/problems/implement-strstr/)

#### Description

Implement [strStr\(\)](http://www.cplusplus.com/reference/cstring/strstr/).

Return the index of the first occurrence of needle in haystack, or **-1** if needle is not part of haystack.

**Example 1:**

```text
Input: haystack = "hello", needle = "ll"
Output: 2
```

**Example 2:**

```text
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

**Clarification:**

What should we return when `needle` is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when `needle` is an empty string. This is consistent to C's [strstr\(\)](http://www.cplusplus.com/reference/cstring/strstr/) and Java's \[indexOf\(\)\]\([https://docs.oracle.com/javase/7/docs/api/java/lang/String.html\#indexOf\(java.lang.String](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf%28java.lang.String)\)\).

#### Solution

Use built-in functions

`haystack.find(needle)` or

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        return haystack.index(needle) if needle in haystack else -1
```

### 242. Valid Anagram\[E\]

[https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)

#### Description

Given two strings _s_ and _t_ , write a function to determine if _t_ is an anagram of _s_.

**Example 1:**

```text
Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2:**

```text
Input: s = "rat", t = "car"
Output: false
```

**Note:** You may assume the string contains only lowercase alphabets.

**Follow up:** What if the inputs contain unicode characters? How would you adapt your solution to such case?

#### Solution

[https://leetcode.com/problems/valid-anagram/solution/](https://leetcode.com/problems/valid-anagram/solution/)

```python

```

### 383. Ransom Note\[E\]

[https://leetcode.com/problems/ransom-note/](https://leetcode.com/problems/ransom-note/)

#### Description

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

**Example 1:**

```text
Input: ransomNote = "a", magazine = "b"
Output: false
```

**Example 2:**

```text
Input: ransomNote = "aa", magazine = "ab"
Output: false
```

**Example 3:**

```text
Input: ransomNote = "aa", magazine = "aab"
Output: true
```

**Constraints:**

* You may assume that both strings contain only lowercase letters.

#### Solution

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        letter_map = {}
        for letter in magazine:
            letter_map[letter] = letter_map.get(letter, 0) + 1
        for letter in ransomNote:
            letter_map[letter] = letter_map.get(letter, 0) - 1
            if letter_map[letter] < 0:
                return False
        return True
```

### 387. First Unique Character in a String\[E\]

[https://leetcode.com/problems/first-unique-character-in-a-string/](https://leetcode.com/problems/first-unique-character-in-a-string/)

#### Description

Given a string, find the first non-repeating character in it and return its index. If it doesn't exist, return -1.

**Examples:**

```text
s = "leetcode"
return 0.

s = "loveleetcode"
return 2.
```

**Note:** You may assume the string contains only lowercase English letters.

#### Solution

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        count_map = {}
        for c in s:
            count_map[c] = count_map.get(c, 0) + 1
        for i, c in enumerate(s):
            if count_map[c] == 1:
                return i
        return -1
```

### 389. Find the Difference\[E\]

[https://leetcode.com/problems/find-the-difference/](https://leetcode.com/problems/find-the-difference/)

#### Description

Given two strings _**s\**_ and _**t\**_ which consist of only lowercase letters.

String _**t\**_ is generated by random shuffling string _**s\**_ and then add one more letter at a random position.

Find the letter that was added in _**t\**_.

**Example:**

```text
Input:
s = "abcd"
t = "abcde"

Output:
e

Explanation:
'e' is the letter that was added.
```

#### Solution

```python
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        res = ord(t[-1])
        for i in range(len(s)):
            res += ord(t[i])
            res -= ord(s[i])
        return chr(res)
```

### 415. Add Strings\[E\]

[https://leetcode.com/problems/add-strings/](https://leetcode.com/problems/add-strings/)

#### Description

Given two non-negative integers `num1` and `num2` represented as string, return the sum of `num1` and `num2`.

**Note:**

1. The length of both `num1` and `num2` is &lt; 5100.
2. Both `num1` and `num2` contains only digits `0-9`.
3. Both `num1` and `num2` does not contain any leading zero.
4. You **must not use any built-in BigInteger library** or **convert the inputs to integer** directly.

#### Solution

```python

```

### 438. Find All Anagrams in a String\[M\]

[https://leetcode.com/problems/find-all-anagrams-in-a-string/](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

#### Description

iven a string **s** and a **non-empty** string **p**, find all the start indices of **p**'s anagrams in **s**.

Strings consists of lowercase English letters only and the length of both strings **s** and **p** will not be larger than 20,100.

The order of output does not matter.

**Example 1:**

```text
Input:
s: "cbaebabacd" p: "abc"

Output:
[0, 6]

Explanation:
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```

**Example 2:**

```text
Input:
s: "abab" p: "ab"

Output:
[0, 1, 2]

Explanation:
The substring with start index = 0 is "ab", which is an anagram of "ab".
The substring with start index = 1 is "ba", which is an anagram of "ab".
The substring with start index = 2 is "ab", which is an anagram of "ab".
```

#### Solution

```python

```

### 459. Repeated Substring Pattern

[https://leetcode.com/problems/repeated-substring-pattern/](https://leetcode.com/problems/repeated-substring-pattern/)

#### Description

Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.

**Example 1:**

```text
Input: "abab"
Output: True
Explanation: It's the substring "ab" twice.
```

**Example 2:**

```text
Input: "aba"
Output: False
```

**Example 3:**

```text
Input: "abcabcabcabc"
Output: True
Explanation: It's the substring "abc" four times. (And the substring "abcabc" twice.)
```

#### Solution

hahaha

```python
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:
        return s in (2 * s)[1:-1]
```

### 709. To Lower Cases\[E\]

[https://leetcode.com/problems/to-lower-case/](https://leetcode.com/problems/to-lower-case/)

#### Description

Implement function ToLowerCase\(\) that has a string parameter str, and returns the same string in lowercase.

**Example 1:**

```text
Input: "Hello"
Output: "hello"
```

**Example 2:**

```text
Input: "here"
Output: "here"
```

**Example 3:**

```text
Input: "LOVELY"
Output: "lovely"
```

#### Solution

```python
class Solution:
    def toLowerCase(self, str: str) -> str:
        lower = ""
        for i in str:
            if 65 <= ord(i) < 97:
                lower += chr(ord(i) + 32)
            else:
                lower += i
        return lower
# str.lower()
```

### 771. Jewels and Stones\[E\]

[https://leetcode.com/problems/jewels-and-stones/](https://leetcode.com/problems/jewels-and-stones/)

#### Description

You're given strings `J` representing the types of stones that are jewels, and `S` representing the stones you have. Each character in `S` is a type of stone you have. You want to know how many of the stones you have are also jewels.

The letters in `J` are guaranteed distinct, and all characters in `J` and `S` are letters. Letters are case sensitive, so `"a"` is considered a different type of stone from `"A"`.

**Example 1:**

```text
Input: J = "aA", S = "aAAbbbb"
Output: 3
```

**Example 2:**

```text
Input: J = "z", S = "ZZ"
Output: 0
```

**Note:**

* `S` and `J` will consist of letters and have length at most 50.
* The characters in `J` are distinct.

#### Solution

```python
class Solution:
    def numJewelsInStones(self, J: str, S: str) -> int:
        jewels = 0
        for stone in S:
            if stone in J:
                jewels = jewels + 1
        return jewels
```

### 811. Subdomain Visit Count\[E\]

[https://leetcode.com/problems/subdomain-visit-count/](https://leetcode.com/problems/subdomain-visit-count/)

#### Description

A website domain like "discuss.leetcode.com" consists of various subdomains. At the top level, we have "com", at the next level, we have "leetcode.com", and at the lowest level, "discuss.leetcode.com". When we visit a domain like "discuss.leetcode.com", we will also visit the parent domains "leetcode.com" and "com" implicitly.

Now, call a "count-paired domain" to be a count \(representing the number of visits this domain received\), followed by a space, followed by the address. An example of a count-paired domain might be "9001 discuss.leetcode.com".

We are given a list `cpdomains` of count-paired domains. We would like a list of count-paired domains, \(in the same format as the input, and in any order\), that explicitly counts the number of visits to each subdomain.

```text
Example 1:
Input: 
["9001 discuss.leetcode.com"]
Output: 
["9001 discuss.leetcode.com", "9001 leetcode.com", "9001 com"]
Explanation: 
We only have one website domain: "discuss.leetcode.com". As discussed above, the subdomain "leetcode.com" and "com" will also be visited. So they will all be visited 9001 times.
Example 2:
Input: 
["900 google.mail.com", "50 yahoo.com", "1 intel.mail.com", "5 wiki.org"]
Output: 
["901 mail.com","50 yahoo.com","900 google.mail.com","5 wiki.org","5 org","1 intel.mail.com","951 com"]
Explanation: 
We will visit "google.mail.com" 900 times, "yahoo.com" 50 times, "intel.mail.com" once and "wiki.org" 5 times. For the subdomains, we will visit "mail.com" 900 + 1 = 901 times, "com" 900 + 50 + 1 = 951 times, and "org" 5 times.
```

**Notes:**

* The length of `cpdomains` will not exceed `100`. 
* The length of each domain name will not exceed `100`.
* Each address will have either 1 or 2 "." characters.
* The input count in any count-paired domain will not exceed `10000`.
* The answer output can be returned in any order.

#### Solution

[https://leetcode.com/problems/subdomain-visit-count/solution/](https://leetcode.com/problems/subdomain-visit-count/solution/)

ttps://leetcode.com/problems/subdomain-visit-count/discuss/121770/Python-short-and-understandable-solution-68-ms

```python

```

### 844. Backspace String Compare\[E\]

[https://leetcode.com/problems/backspace-string-compare/](https://leetcode.com/problems/backspace-string-compare/)

#### Description

Given two strings `S` and `T`, return if they are equal when both are typed into empty text editors. `#` means a backspace character.

Note that after backspacing an empty text, the text will continue empty.

**Example 1:**

```text
Input: S = "ab#c", T = "ad#c"
Output: true
Explanation: Both S and T become "ac".
```

**Example 2:**

```text
Input: S = "ab##", T = "c#d#"
Output: true
Explanation: Both S and T become "".
```

**Example 3:**

```text
Input: S = "a##c", T = "#a#c"
Output: true
Explanation: Both S and T become "c".
```

**Example 4:**

```text
Input: S = "a#c", T = "b"
Output: false
Explanation: S becomes "c" while T becomes "b".
```

**Note**:

* `1 <= S.length <= 200`
* `1 <= T.length <= 200`
* `S` and `T` only contain lowercase letters and `'#'` characters.

**Follow up:**

* Can you solve it in `O(N)` time and `O(1)` space?

#### Solution

[https://leetcode.com/problems/backspace-string-compare/solution/](https://leetcode.com/problems/backspace-string-compare/solution/)

```python

```

### 929. Unique Email Addresses\[E\]

[https://leetcode.com/problems/unique-email-addresses/](https://leetcode.com/problems/unique-email-addresses/)

#### Description

Every email consists of a local name and a domain name, separated by the @ sign.

For example, in `alice@leetcode.com`, `alice` is the local name, and `leetcode.com` is the domain name.

Besides lowercase letters, these emails may contain `'.'`s or `'+'`s.

If you add periods \(`'.'`\) between some characters in the **local name** part of an email address, mail sent there will be forwarded to the same address without dots in the local name. For example, `"alice.z@leetcode.com"` and `"alicez@leetcode.com"` forward to the same email address. \(Note that this rule does not apply for domain names.\)

If you add a plus \(`'+'`\) in the **local name**, everything after the first plus sign will be **ignored**. This allows certain emails to be filtered, for example `m.y+name@email.com` will be forwarded to `my@email.com`. \(Again, this rule does not apply for domain names.\)

It is possible to use both of these rules at the same time.

Given a list of `emails`, we send one email to each address in the list. How many different addresses actually receive mails?

**Example 1:**

```text
Input: ["test.email+alex@leetcode.com","test.e.mail+bob.cathy@leetcode.com","testemail+david@lee.tcode.com"]
Output: 2
Explanation: "testemail@leetcode.com" and "testemail@lee.tcode.com" actually receive mails
```

**Note:**

* `1 <= emails[i].length <= 100`
* `1 <= emails.length <= 100`
* Each `emails[i]` contains exactly one `'@'` character.
* All local and domain names are non-empty.
* Local names do not start with a `'+'` character.

#### Solution

[https://leetcode.com/problems/unique-email-addresses/solution/](https://leetcode.com/problems/unique-email-addresses/solution/)

```python

```

### 937. Reorder Data in Log Files\[E\]

[https://leetcode.com/problems/reorder-data-in-log-files/](https://leetcode.com/problems/reorder-data-in-log-files/)

#### Description

You have an array of `logs`. Each log is a space delimited string of words.

For each log, the first word in each log is an alphanumeric _identifier_. Then, either:

* Each word after the identifier will consist only of lowercase letters, or;
* Each word after the identifier will consist only of digits.

We will call these two varieties of logs _letter-logs_ and _digit-logs_. It is guaranteed that each log has at least one word after its identifier.

Reorder the logs so that all of the letter-logs come before any digit-log. The letter-logs are ordered lexicographically ignoring identifier, with the identifier used in case of ties. The digit-logs should be put in their original order.

Return the final order of the logs.

**Example 1:**

```text
Input: logs = ["dig1 8 1 5 1","let1 art can","dig2 3 6","let2 own kit dig","let3 art zero"]
Output: ["let1 art can","let3 art zero","let2 own kit dig","dig1 8 1 5 1","dig2 3 6"]
```

**Constraints:**

1. `0 <= logs.length <= 100`
2. `3 <= logs[i].length <= 100`
3. `logs[i]` is guaranteed to have an identifier, and a word after the identifier.

#### Solution

[https://leetcode.com/problems/reorder-data-in-log-files/solution/](https://leetcode.com/problems/reorder-data-in-log-files/solution/)

```python

```

### 953. Verifying an Alien Dictionary\[E\]

[https://leetcode.com/problems/verifying-an-alien-dictionary/](https://leetcode.com/problems/verifying-an-alien-dictionary/)

#### Description

In an alien language, surprisingly they also use english lowercase letters, but possibly in a different `order`. The `order` of the alphabet is some permutation of lowercase letters.

Given a sequence of `words` written in the alien language, and the `order` of the alphabet, return `true` if and only if the given `words` are sorted lexicographicaly in this alien language.

**Example 1:**

```text
Input: words = ["hello","leetcode"], order = "hlabcdefgijkmnopqrstuvwxyz"
Output: true
Explanation: As 'h' comes before 'l' in this language, then the sequence is sorted.
```

**Example 2:**

```text
Input: words = ["word","world","row"], order = "worldabcefghijkmnpqstuvxyz"
Output: false
Explanation: As 'd' comes after 'l' in this language, then words[0] > words[1], hence the sequence is unsorted.
```

**Example 3:**

```text
Input: words = ["apple","app"], order = "abcdefghijklmnopqrstuvwxyz"
Output: false
Explanation: The first three characters "app" match, and the second string is shorter (in size.) According to lexicographical rules "apple" > "app", because 'l' > '∅', where '∅' is defined as the blank character which is less than any other character (More info).
```

**Constraints:**

* `1 <= words.length <= 100`
* `1 <= words[i].length <= 20`
* `order.length == 26`
* All characters in `words[i]` and `order` are English lowercase letters.

#### Solution

[https://leetcode.com/problems/verifying-an-alien-dictionary/solution/](https://leetcode.com/problems/verifying-an-alien-dictionary/solution/)

```python

```

