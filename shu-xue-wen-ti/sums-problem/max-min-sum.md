# Max-Min Sum



### 373. Find K Pairs with Smallest Sums\[M\]

[https://leetcode.com/problems/find-k-pairs-with-smallest-sums/](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)

#### Description

You are given two integer arrays **nums1** and **nums2** sorted in ascending order and an integer **k**.

Define a pair **\(u,v\)** which consists of one element from the first array and one element from the second array.

Find the k pairs **\(u1,v1\),\(u2,v2\) ...\(uk,vk\)** with the smallest sums.

**Example 1:**

```text
Input: nums1 = [1,7,11], nums2 = [2,4,6], k = 3
Output: [[1,2],[1,4],[1,6]] 
Explanation: The first 3 pairs are returned from the sequence: 
             [1,2],[1,4],[1,6],[7,2],[7,4],[11,2],[7,6],[11,4],[11,6]
```

**Example 2:**

```text
Input: nums1 = [1,1,2], nums2 = [1,2,3], k = 2
Output: [1,1],[1,1]
Explanation: The first 2 pairs are returned from the sequence: 
             [1,1],[1,1],[1,2],[2,1],[1,2],[2,2],[1,3],[1,3],[2,3]
```

**Example 3:**

```text
Input: nums1 = [1,2], nums2 = [3], k = 3
Output: [1,3],[2,3]
Explanation: All possible pairs are returned from the sequence: [1,3],[2,3]
```

#### Solution

[https://discuss.leetcode.com/topic/50450/slow-1-liner-to-fast-solutions](https://discuss.leetcode.com/topic/50450/slow-1-liner-to-fast-solutions)

```python

```

### 416. Partition Equal Subset Sum\[M\]

[https://leetcode.com/problems/partition-equal-subset-sum/](https://leetcode.com/problems/partition-equal-subset-sum/)

#### Description

Given a **non-empty** array containing **only positive integers**, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.

**Note:**

1. Each of the array element will not exceed 100.
2. The array size will not exceed 200.

**Example 1:**

```text
Input: [1, 5, 11, 5]

Output: true

Explanation: The array can be partitioned as [1, 5, 5] and [11].
```

**Example 2:**

```text
Input: [1, 2, 3, 5]

Output: false

Explanation: The array cannot be partitioned into equal sum subsets.
```

#### Solution

```python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        total_sum = sum(nums)
        if total_sum & 1:
            return False
        # if sum of some elements can be half of total sum then true
        target = total_sum >> 1
        dp = [0] * (target + 1)
        dp[0] = 1
        for num in nums:
            for i in range(target, num - 1, -1):
                dp[i] = dp[i] | dp[i - num]
        return dp[target] == 1
```

