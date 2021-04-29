# permutations



### 46. Permutations\[M\]

[https://leetcode.com/problems/permutations/](https://leetcode.com/problems/permutations/)

#### Description

Given a collection of **distinct** integers, return all possible permutations.

**Example:**

```text
Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

#### Solution

```python

```

### 47. Permutations II\[M\]

#### Description

Given a collection of numbers that might contain duplicates, return all possible unique permutations.

**Example:**

```text
Input: [1,1,2]
Output:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```

#### Solution

```python

```

### 31. Next Permutation\[M\]

[https://leetcode.com/problems/next-permutation/](https://leetcode.com/problems/next-permutation/)

#### Description

Implement **next permutation**, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order \(ie, sorted in ascending order\).

The replacement must be [**in-place**](http://en.wikipedia.org/wiki/In-place_algorithm) and use only constant extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.

```text
1,2,3` → `1,3,2`
`3,2,1` → `1,2,3`
`1,1,5` → `1,5,1
```

#### Solution

### 60. Permutation Sequence\[H\]

[https://leetcode.com/problems/permutation-sequence/](https://leetcode.com/problems/permutation-sequence/)

#### Description

The set `[1,2,3,...,*n*]` contains a total of _n_! unique permutations.

By listing and labeling all of the permutations in order, we get the following sequence for _n_ = 3:

1. `"123"`
2. `"132"`
3. `"213"`
4. `"231"`
5. `"312"`
6. `"321"`

Given _n_ and _k_, return the _k_th permutation sequence.

**Note:**

* Given _n_ will be between 1 and 9 inclusive.
* Given _k_ will be between 1 and _n_! inclusive.

**Example 1:**

```text
Input: n = 3, k = 3
Output: "213"
```

**Example 2:**

```text
Input: n = 4, k = 9
Output: "2314"
```

#### Solution

```python

```

### 784. Letter Case Permutation\[E\]

[https://leetcode.com/problems/letter-case-permutation/](https://leetcode.com/problems/letter-case-permutation/)

#### Description

Given a string S, we can transform every letter individually to be lowercase or uppercase to create another string. Return a list of all possible strings we could create.

```text
Examples:
Input: S = "a1b2"
Output: ["a1b2", "a1B2", "A1b2", "A1B2"]

Input: S = "3z4"
Output: ["3z4", "3Z4"]

Input: S = "12345"
Output: ["12345"]
```

**Note:**

* `S` will be a string with length between `1` and `12`.
* `S` will consist only of letters or digits.

#### Solution

```python
class Solution:
    def letterCasePermutation(self, S: str) -> List[str]:
        B = sum(letter.isalpha() for letter in S)
        ans = []

        for bits in xrange(1 << B):
            b = 0
            word = []
            for letter in S:
                if letter.isalpha():
                    if (bits >> b) & 1:
                        word.append(letter.lower())
                    else:
                        word.append(letter.upper())

                    b += 1
                else:
                    word.append(letter)

            ans.append("".join(word))
        return ans
```

### 567. Permutation in String\[M\]

[https://leetcode.com/problems/permutation-in-string/](https://leetcode.com/problems/permutation-in-string/)

#### Description

iven two strings **s1** and **s2**, write a function to return true if **s2** contains the permutation of **s1**. In other words, one of the first string's permutations is the **substring** of the second string.

**Example 1:**

```text
Input: s1 = "ab" s2 = "eidbaooo"
Output: True
Explanation: s2 contains one permutation of s1 ("ba").
```

**Example 2:**

```text
Input:s1= "ab" s2 = "eidboaoo"
Output: False
```

**Constraints:**

* The input strings only contain lower case letters.
* The length of both given strings is in range \[1, 10,000\].

#### Solution

```python

```

