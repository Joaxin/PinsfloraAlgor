# Misc



### 4. Median of Two Sorted Arrays\[H\]

[https://leetcode.com/problems/median-of-two-sorted-arrays/](https://leetcode.com/problems/median-of-two-sorted-arrays/)

#### Description

There are two sorted arrays **nums1** and **nums2** of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O\(log \(m+n\)\).

You may assume **nums1** and **nums2** cannot be both empty.

**Example 1:**

```text
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```

**Example 2:**

```text
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

#### Solution

```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        nums = sorted(nums1 + nums2)
        idx = len(nums)
        return nums[idx//2] if idx % 2 else (nums[idx//2 - 1] + nums[idx//2])/2
```

But the overall run time complexity should be O\(log \(m+n\)\), so it’s not the way.

[https://leetcode.com/problems/median-of-two-sorted-arrays/solution/](https://leetcode.com/problems/median-of-two-sorted-arrays/solution/)

[https://leetcode.com/problems/median-of-two-sorted-arrays/discuss/2471/Very-concise-O\(log\(min\(MN\)\)\)-iterative-solution-with-detailed-explanation](https://leetcode.com/problems/median-of-two-sorted-arrays/discuss/2471/Very-concise-O%28log%28min%28MN%29%29%29-iterative-solution-with-detailed-explanation)

```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        N1, N2 = len(nums1), len(nums2)
        if N1 < N2: 
            nums1, N1, nums2, N2 = nums2, N2, nums1, N1
        l, r = 0, N2*2
        while l <= r:
            j = (l + r) >> 1
            i = N1 + N2 - j
            L1 = -sys.maxsize-1 if i == 0 else nums1[(i-1)>>1]
            L2 = -sys.maxsize-1 if j == 0 else nums2[(j-1)>>1]
            R1 = sys.maxsize if i == 2*N1 else nums1[i>>1]
            R2 = sys.maxsize if j == 2*N2 else nums2[j>>1]
            if L1 > R2: l = j + 1
            elif L2 > R1: r = j - 1
            else:
                return (max(L1, L2) + min(R1, R2))/2.0
```

### 128. Longest Consecutive Sequence\[H\]

[https://leetcode.com/problems/longest-consecutive-sequence/](https://leetcode.com/problems/longest-consecutive-sequence/)

#### Description

Given an unsorted array of integers, find the length of the longest consecutive elements sequence.

Your algorithm should run in O\(_n_\) complexity.

**Example:**

```text
Input: [100, 4, 200, 1, 3, 2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
```

#### Solution

[https://leetcode.com/problems/longest-consecutive-sequence/solution/](https://leetcode.com/problems/longest-consecutive-sequence/solution/)

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        num = set(nums)
        maxLen = 0
        while num:
            n = num.pop()
            i = n + 1
            l1 = 0
            l2 = 0
            while i in num:
                num.remove(i)
                i += 1
                l1 += 1
            i = n - 1
            while i in num:
                num.remove(i)
                i -= 1
                l2 += 1
            maxLen = max(maxLen, l1 + l2 + 1)
        return maxLen
```

### 674. Longest Continuous Increasing Subsequence\[E\]

[https://leetcode.com/problems/longest-continuous-increasing-subsequence/](https://leetcode.com/problems/longest-continuous-increasing-subsequence/)

#### Description

Given an unsorted array of integers, find the length of longest `continuous` increasing subsequence \(subarray\).

**Example 1:**

```text
Input: [1,3,5,4,7]
Output: 3
Explanation: The longest continuous increasing subsequence is [1,3,5], its length is 3. 
Even though [1,3,5,7] is also an increasing subsequence, it's not a continuous one where 5 and 7 are separated by 4.
```

**Example 2:**

```text
Input: [2,2,2,2,2]
Output: 1
Explanation: The longest continuous increasing subsequence is [2], its length is 1.
```

**Note:** Length of the array will not exceed 10,000.

#### Solution

[https://leetcode.com/problems/longest-continuous-increasing-subsequence/solution/](https://leetcode.com/problems/longest-continuous-increasing-subsequence/solution/)

```python
class Solution:
    def findLengthOfLCIS(self, nums: List[int]) -> int:
        if not nums or len(nums) == 0:
            return 0
        ans = curr = 1
        for i in range(len(nums) - 1):
            if nums[i] < nums[i + 1]:
                curr += 1
                ans = max(ans, curr)
            else:
                curr = 1
        return ans
```

