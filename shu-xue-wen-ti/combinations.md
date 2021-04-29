# Combinations



$$C_M^N =\frac{M!}{N!(M-N)!}, \text{(M=4, N=2)}$$

### 77. Combinations\[E\]

[https://leetcode.com/problems/combinations/](https://leetcode.com/problems/combinations/)

#### Description

Given two integers _n_ and _k_, return all possible combinations of _k_ numbers out of 1 ... _n_.

**Example:**

```text
Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

#### Solution

```python
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        import itertools as it
        return [list(x) for x in list(it.combinations([i for i in range(1,n+1)], k))]
```

