# First Missing Positive

###  41. First Missing Positive\[H\]

[https://leetcode.com/problems/first-missing-positive/](https://leetcode.com/problems/first-missing-positive/)

#### Description

Given an **unsorted** integer array, find the smallest missing positive integer.

**Example 1:**

```text
 Input: [1,2,0]
 Output: 3
```

**Example 2:**

```text
 Input: [3,4,-1,1]
 Output: 2
```

**Example 3:**

```text
 Input: [7,8,9,11,12]
 Output: 1
```

**Note:**

Your algorithm should run in _O_\(_n_\) time and uses constant extra space.

#### Solution

[https://leetcode.com/problems/first-missing-positive/discuss/17080/Python-O\(1\)-space-O\(n\)-time-solution-with-explanation](https://leetcode.com/problems/first-missing-positive/discuss/17080/Python-O%281%29-space-O%28n%29-time-solution-with-explanation)

```text
 def firstMissingPositive(self, nums: List[int]) -> int:
     """
     For nums with length n, the possible result is in the range of
     [1 : n + 1], we want to know the smallest integer in the range 
     of [1 : n] that is not in nums, if [1 : n] are all in nums,
     the result is n + 1
 ​
     So those numbers not in [1 : n] are not useful and we can just
     change them to be 0
 ​
     Then we go through nums, if nums[i] is in the range of 
     [1 : n], we use index (nums[i] - 1) to record that we have
     seen nums[i] by adding n + 1 to nums[nums[i] - 1]
 ​
     Finally we just need to find the first index i for which 
     nums[i] is less than n + 1 (which means we never met number
     i + 1 so we did not add n + 1 to nums[i])
     e.g.
 ​
     """
     n = len(nums)
     for i in range(n):
         if nums[i] < 1 or nums[i] > n:
             nums[i] = 0
 ​
     for i in range(n):
         if 1 <= nums[i] % (n + 1) <= n:
             ind = nums[i] % (n + 1) - 1
             nums[ind] += n + 1
     for i in range(n):
         if nums[i] <= n:
             return i + 1
     ## [-1,1,2,3,5,9]
     ## [0, 1, 2, 3, 5, 0]
     ## when i=4 note that ind=4
     ## [7, 8, 9, 3, 12, 0]
     return n + 1
```

==&gt;

```text
 class Solution:
     def firstMissingPositive(self, nums: List[int]) -> int:
         n = len(nums)
         for i in range(n):
             if nums[i] < 1 or nums[i] > n:
                 nums[i] = 0
 ​
         for i in range(n):
             if nums[i]:
                 nums[nums[i] % (n + 1) - 1] += n + 1
 ​
         for i in range(n):
             if nums[i] <= n:
                 return i + 1
         return n + 1
```

