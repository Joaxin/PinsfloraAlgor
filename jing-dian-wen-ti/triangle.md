# Triangle



### 120. Triangle\[M\]

[https://leetcode.com/problems/triangle/](https://leetcode.com/problems/triangle/)

#### Description

Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

For example, given the following triangle

```text
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
```

The minimum path sum from top to bottom is `11` \(i.e., **2** + **3** + **5** + **1** = 11\).

**Note:**

Bonus point if you are able to do this using only _O_\(_n_\) extra space, where _n_ is the total number of rows in the triangle.

#### Solution

```python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        if triangle is None or len(triangle) == 0:
            return 0
        ls = len(triangle)
        dp = [0] * ls
        dp[0] = triangle[0][0]
        for i in range(1, ls):
            # note that dp should be updated in reversed order
            dp[i] = dp[i - 1] + triangle[i][i]
            for j in reversed(range(1, i)):
                dp[j] = min(dp[j - 1] + triangle[i][j], dp[j] + triangle[i][j])
            dp[0] = dp[0] + triangle[i][0]
        return min(dp)
```

