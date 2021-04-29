# Frequency



### 347. Top K Frequent Elements\[M\]

[https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)

#### Description

Given a non-empty array of integers, return the _**k\**_ most frequent elements.

**Example 1:**

```text
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**Example 2:**

```text
Input: nums = [1], k = 1
Output: [1]
```

**Note:**

* You may assume _k_ is always valid, 1 ≤ _k_ ≤ number of unique elements.
* Your algorithm's time complexity **must be** better than O\(_n_ log _n_\), where _n_ is the array's size.
* It's guaranteed that the answer is unique, in other words the set of the top k frequent elements is unique.
* You can return the answer in any order.

#### Solution

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        counter = collections.Counter(nums)
        return [k for k,v in counter.most_common(k)]
```

