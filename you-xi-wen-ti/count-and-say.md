# Count and Say

### 38. Count and Say\[E\]

[https://leetcode.com/problems/count-and-say/](https://leetcode.com/problems/count-and-say/)

#### Description

The count-and-say sequence is the sequence of integers with the first five terms as following:

```text
1.     1
2.     11
3.     21
4.     1211
5.     111221
```

`1` is read off as `"one 1"` or `11`. `11` is read off as `"two 1s"` or `21`. `21` is read off as `"one 2`, then `one 1"` or `1211`.

Given an integer _n_ where 1 ≤ _n_ ≤ 30, generate the _n_th term of the count-and-say sequence. You can do so recursively, in other words from the previous member read off the digits, counting the number of digits in groups of the same digit.

Note: Each term of the sequence of integers will be represented as a string.

**Example 1:**

```text
Input: 1
Output: "1"
Explanation: This is the base case.
```

**Example 2:**

```text
Input: 4
Output: "1211"
Explanation: For n = 3 the term was "21" in which we have two groups "2" and "1", "2" can be read as "12" which means frequency = 1 and value = 2, the same way "1" is read as "11", so the answer is the concatenation of "12" and "11" which is "1211".
```

#### Solution

[https://leetcode.com/problems/count-and-say/discuss/16015/Please-change-the-misleading-description](https://leetcode.com/problems/count-and-say/discuss/16015/Please-change-the-misleading-description)

[https://leetcode.com/problems/count-and-say/discuss/15999/4-5-lines-Python-solutions](https://leetcode.com/problems/count-and-say/discuss/15999/4-5-lines-Python-solutions)

```python
class Solution:
    def countAndSay(self, n: int) -> str:
        res = '1'
        for _ in range(n - 1):
            res = re.sub(r'(.)\1*', lambda n: str(len(n.group(0))) + n.group(1), res)
        return res
```

### 443. String Compression\[E\]

[https://leetcode.com/problems/string-compression/](https://leetcode.com/problems/string-compression/)

#### Description

Given an array of characters, compress it [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm).

The length after compression must always be smaller than or equal to the original array.

Every element of the array should be a **character** \(not int\) of length 1.

After you are done **modifying the input array** [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm), return the new length of the array.

**Follow up:** Could you solve it using only O\(1\) extra space?

**Example 1:**

```text
Input:
["a","a","b","b","c","c","c"]

Output:
Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]

Explanation:
"aa" is replaced by "a2". "bb" is replaced by "b2". "ccc" is replaced by "c3".
```

**Example 2:**

```text
Input:
["a"]

Output:
Return 1, and the first 1 characters of the input array should be: ["a"]

Explanation:
Nothing is replaced.
```

**Example 3:**

```text
Input:
["a","b","b","b","b","b","b","b","b","b","b","b","b"]

Output:
Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].

Explanation:
Since the character "a" does not repeat, it is not compressed. "bbbbbbbbbbbb" is replaced by "b12".
Notice each digit has it's own entry in the array.
```

**Note:**

1. All characters have an ASCII value in `[35, 126]`.
2. `1 <= len(chars) <= 1000`.

#### Solution

```python
class Solution:
    def compress(self, chars: List[str]) -> int:
        anchor = write = 0
        l = len(chars)
        for read in range(l):
            if read == l - 1 or chars[read] != chars[read + 1]:
                # finish reading aabbbcc 6==7 - 1 or a!=b
                chars[write] = chars[anchor] # a b c
                write += 1
                if read > anchor:
                    # check if it is the only one
                    for digit in str(read - anchor + 1):
                        chars[write] = digit
                        write += 1
                anchor = read + 1
        return write
```

[https://leetcode.com/problems/string-compression/solution/](https://leetcode.com/problems/string-compression/solution/)

