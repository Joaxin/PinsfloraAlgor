# Combination Sum



### 39. Combination Sum\[M\]

[https://leetcode.com/problems/combination-sum/](https://leetcode.com/problems/combination-sum/)

#### Description

Given a **set** of candidate numbers \(`candidates`\) **\(without duplicates\)** and a target number \(`target`\), find all unique combinations in `candidates` where the candidate numbers sums to `target`.

The **same** repeated number may be chosen from `candidates` unlimited number of times.

**Note:**

* All numbers \(including `target`\) will be positive integers.
* The solution set must not contain duplicate combinations.

**Example 1:**

```text
Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [7],
  [2,2,3]
]
```

**Example 2:**

```text
Input: candidates = [2,3,5], target = 8,
A solution set is:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]
```

**Constraints:**

* `1 <= candidates.length <= 30`
* `1 <= candidates[i] <= 200`
* Each element of `candidate` is unique.
* `1 <= target <= 500`

#### Solution

```python

```

### 40. Combination Sum II\[M\]

[https://leetcode.com/problems/combination-sum-ii/](https://leetcode.com/problems/combination-sum-ii/)

#### Description

Given a collection of candidate numbers \(`candidates`\) and a target number \(`target`\), find all unique combinations in `candidates` where the candidate numbers sums to `target`.

Each number in `candidates` may only be used **once** in the combination.

**Note:**

* All numbers \(including `target`\) will be positive integers.
* The solution set must not contain duplicate combinations.

**Example 1:**

```text
Input: candidates = [10,1,2,7,6,1,5], target = 8,
A solution set is:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
```

**Example 2:**

```text
Input: candidates = [2,5,2,1,2], target = 5,
A solution set is:
[
  [1,2,2],
  [5]
]
```

#### Solution

```python

```

### 216. Combination Sum III\[M\]

[https://leetcode.com/problems/combination-sum-iii/](https://leetcode.com/problems/combination-sum-iii/)

#### Description

Find all possible combinations of _**k**_ numbers that add up to a number _**n**_, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.

**Note:**

* All numbers will be positive integers.
* The solution set must not contain duplicate combinations.

**Example 1:**

```text
Input: k = 3, n = 7
Output: [[1,2,4]]
```

**Example 2:**

```text
Input: k = 3, n = 9
Output: [[1,2,6], [1,3,5], [2,3,4]]
```

#### Solution

```python
import itertools as it
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        return list(filter(lambda x: sum(x) == n, list(it.combinations(range(1, 10), k))))
```

