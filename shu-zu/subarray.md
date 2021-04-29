# Subarray



### 53. Maximum Subarray\[E\]

[https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)

#### Description

given an integer array `nums`, find the contiguous subarray \(containing at least one number\) which has the largest sum and return its sum.

**Example:**

```text
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

**Follow up:**

If you have figured out the O\(_n_\) solution, try coding another solution using the divide and conquer approach, which is more subtle.

子列表元素之和的最大值

说明：子列表指的是列表中索引（下标）连续的元素构成的列表；列表中的元素是int类型，可能包含正整数、0、负整数；程序输入列表中的元素，输出子列表元素求和的最大值，例如：

输入：1 -2 3 5 -3 2

输出：8

输入：0 -2 3 5 -1 2

输出：9

输入：-9 -2 -3 -5 -3

输出：-2

#### Solution

[https://leetcode.com/problems/maximum-subarray/discuss/20396/Easy-Python-Way](https://leetcode.com/problems/maximum-subarray/discuss/20396/Easy-Python-Way)

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        for i in range(1, len(nums)):
                if nums[i-1] > 0:
                    nums[i] += nums[i-1]
        return max(nums)
```

```python
## 动态规划例子

items = list(map(int, input().split()))
overall = partial = items[0]
for i in range(1, len(items)):
    partial = max(items[i], partial + items[i])
    overall = max(partial, overall)
print(overall)
```

> **说明**：这个题目最容易想到的解法是使用二重循环，但是代码的时间性能将会变得非常的糟糕。使用动态规划的思想，仅仅是多用了两个变量，就将原来$O\(N^2\)$复杂度的问题变成了$O\(N\)$。

### 152. Maximum Product Subarray\[M\]

[https://leetcode.com/problems/maximum-product-subarray/](https://leetcode.com/problems/maximum-product-subarray/)

#### Description

Given an integer array `nums`, find the contiguous subarray within an array \(containing at least one number\) which has the largest product.

**Example 1:**

```text
Input: [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.
```

**Example 2:**

```text
Input: [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not a subarray.
```

#### Solution

### 560. Subarray Sum Equals K\[M\]

[https://leetcode.com/problems/subarray-sum-equals-k/](https://leetcode.com/problems/subarray-sum-equals-k/)

#### Description

Given an array of integers and an integer **k**, you need to find the total number of continuous subarrays whose sum equals to **k**.

**Example 1:**

```text
Input:nums = [1,1,1], k = 2
Output: 2
```

**Constraints:**

* The length of the array is in range \[1, 20,000\].
* The range of numbers in the array is \[-1000, 1000\] and the range of the integer **k** is \[-1e7, 1e7\].

#### Solution

[https://leetcode.com/problems/subarray-sum-equals-k/solution/](https://leetcode.com/problems/subarray-sum-equals-k/solution/)

```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        kmap = {}
        kmap[0] = 1
        count = s = 0
        for num in nums:
            s += num
            count += kmap.get(s - k, 0)
            kmap[s] = kmap.get(s, 0) + 1
        return count
```

### 713. Subarray Product Less Than K\[M\]

[https://leetcode.com/problems/subarray-product-less-than-k/](https://leetcode.com/problems/subarray-product-less-than-k/)

#### Description

Your are given an array of positive integers `nums`.

Count and print the number of \(contiguous\) subarrays where the product of all the elements in the subarray is less than `k`.

**Example 1:**

```text
Input: nums = [10, 5, 2, 6], k = 100
Output: 8
Explanation: The 8 subarrays that have product less than 100 are: [10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6].
Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.
```

**Note:**

`0 < nums.length <= 50000`.

`0 < nums[i] < 1000`.

`0 <= k < 10^6`.

#### Solution

```python

```

[https://leetcode.com/problems/subarray-product-less-than-k/solution/](https://leetcode.com/problems/subarray-product-less-than-k/solution/)

### 581. Shortest Unsorted Continuous Subarray\[E\]

[https://leetcode.com/problems/shortest-unsorted-continuous-subarray/](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/)

#### Description

Given an integer array, you need to find one **continuous subarray** that if you only sort this subarray in ascending order, then the whole array will be sorted in ascending order, too.

You need to find the **shortest** such subarray and output its length.

**Example 1:**

```text
Input: [2, 6, 4, 8, 10, 9, 15]
Output: 5
Explanation: You need to sort [6, 4, 8, 10, 9] in ascending order to make the whole array sorted in ascending order.
```

**Note:**

1. Then length of the input array is in range \[1, 10,000\].
2. The input array may contain duplicates, so ascending order here means **&lt;=**.

#### Solution

```python

```

### 974. Subarray Sums Divisible by K\[M\]

[https://leetcode.com/problems/subarray-sums-divisible-by-k/](https://leetcode.com/problems/subarray-sums-divisible-by-k/)

#### Description

iven an array `A` of integers, return the number of \(contiguous, non-empty\) subarrays that have a sum divisible by `K`.

**Example 1:**

```text
Input: A = [4,5,0,-2,-3,1], K = 5
Output: 7
Explanation: There are 7 subarrays with a sum divisible by K = 5:
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]
```

**Note:**

1. `1 <= A.length <= 30000`
2. `-10000 <= A[i] <= 10000`
3. `2 <= K <= 10000`

#### Solution

```python

```

