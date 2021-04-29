# Misc

### 228. Summary Ranges\[M\]

[https://leetcode.com/problems/summary-ranges/](https://leetcode.com/problems/summary-ranges/)

#### Description

给定一个无重复元素的有序整数数组 `nums` 。

返回 **恰好覆盖数组中所有数字** 的 **最小有序** 区间范围列表。也就是说，`nums` 的每个元素都恰好被某个区间范围所覆盖，并且不存在属于某个范围但不属于 `nums` 的数字 `x` 。

Given a sorted integer array without duplicates, return the summary of its ranges.

**Example 1:**

```text
 Input:  [0,1,2,4,5,7]
 Output: ["0->2","4->5","7"]
 Explanation: 0,1,2 form a continuous range; 4,5 form a continuous range.
```

**Example 2:**

```text
 Input:  [0,2,3,4,6,8,9]
 Output: ["0","2->4","6","8->9"]
 Explanation: 2,3,4 form a continuous range; 8,9 form a continuous range.
```

#### Solution

```text
 class Solution:
     def summaryRanges(self, nums: List[int]) -> List[str]:
         res = []
         start, ls = 0, len(nums)
         for i in range(ls):
             if i + 1 <  ls and nums[i + 1] == nums[i] + 1:
                 continue
             if i == start:
                 res.append(str(nums[start]))
             else:
                 res.append("%d->%d" % (nums[start], nums[i]))
             start = i + 1
         return res
 ​
```

#### 

