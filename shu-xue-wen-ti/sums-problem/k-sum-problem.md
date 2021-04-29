# K SUM Problem



### 1. Two Sum

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

#### Description

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the _same_ element twice.

**Example:**

```text
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

#### Solution

My solution, intelligible brutal force\(O\(n2\), _O_\(1\)\) but not fast:

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i, num1 in enumerate(nums):
            for j, num2 in enumerate(nums[i + 1:]):
                if num1 +  num2 == target:
                    return [i, j + i + 1]
```

**OR**

```python
 class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i, j]
```

From [https://leetcode.com/problems/two-sum/solution/](https://leetcode.com/problems/two-sum/solution/), and I added some notes:

```python
class Solution:
    def twoSum(self, nums, target):
        # h represents hash table, in py, it's simple dictionary here
        # let it be twoSum([5, 2, 1], 3)
        # 1st --> h = {5:0}
        # 2nd --> h = {5: 0, 2: 1}
        # 3rd --> return [1,2]
        h = {} 
        for i, num in enumerate(nums):
            # direct lookup if exists in h
            if target - num in h:
                return [h[target - num], i]
            # store numbers and indices if not in h
            h[num] = i
```

Then, same as in JavaScript:

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
// twoSum([5, 2, 1], 3)
// {-2: 0} -- {1: 1, -2: 0} -- return [1,2]
var twoSum = function(nums, target) {
    const comp = {};
    for (let i = 0; i < nums.length; i++) {
        if (comp[nums[i]] >= 0) {
            return [comp[nums[i]], i]
        }
        comp[target - nums[i]] = i
        // console.log(comp)
    }
};
```

### 167. Two Sum II - Input array is sorted

[https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

#### Description

Given an array of integers that is already _**sorted in ascending order\**_, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

**Note:**

* Your returned answers \(both index1 and index2\) are not zero-based.
* You may assume that each input would have _exactly_ one solution and you may not use the _same_ element twice.

**Example:**

```text
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
```

#### Solution

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        begin, end = 0, len(numbers) - 1
        while begin < end:
            curr = numbers[begin] + numbers[end]
            if curr == target:
                return [begin + 1, end + 1]
            elif curr < target:
                begin += 1
            else:
                end -= 1
```

### 15. 3Sum

[https://leetcode.com/problems/3sum/](https://leetcode.com/problems/3sum/)

#### Description

Given an array `nums` of _n_ integers, are there elements _a_, _b_, _c_ in `nums` such that _a_ + _b_ + _c_ = 0? Find all unique triplets in the array which gives the sum of zero.

**Note:**

The solution set must not contain duplicate triplets.

**Example:**

```text
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

#### Solution

I tried this:

```python
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        for i, num1 in enumerate(nums):
            for j, num2 in enumerate(nums[i+1:]):
                if - num1 - num2 in nums[i+1+j+1:]:
                    res.append(tuple(sorted([num1, num2, - num1 - num2])))
        return [list(j) for j in set(res)]
```

| **311 / 313** test cases passed. | Status: Time Limit Exceeded |
| :--- | :--- |
| Last executed input: | **\[82597,-9243,62390,83030,..\]** |

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()
        lst = len(nums)
        for i in range(lst - 2):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            j = i + 1
            k = lst - 1
            while j < k:
                curr = nums[i] + nums[j] + nums[k]
                if curr == 0:
                    res.append([nums[i], nums[j], nums[k]])
                    while j < k and nums[j] == nums[j + 1]:
                        j += 1
                    while j < k and nums[k] == nums[k - 1]:
                        k -= 1
                    j += 1
                    k -= 1
                elif curr < 0:
                    j += 1
                else:
                    k -= 1
        return res
```

### 16. 3Sum Closest

[https://leetcode.com/problems/3sum-closest/](https://leetcode.com/problems/3sum-closest/)

#### Description

Given an array `nums` of _n_ integers and an integer `target`, find three integers in `nums` such that the sum is closest to `target`. Return the sum of the three integers. You may assume that each input would have exactly one solution.

**Example 1:**

```text
Input: nums = [-1,2,1,-4], target = 1
Output: 2
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

**Constraints:**

* `3 <= nums.length <= 10^3`
* `-10^3 <= nums[i] <= 10^3`
* `-10^4 <= target <= 10^4`

#### Solution

```python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        ls = len(nums)
        sort_nums = sorted(nums)
        res = nums[0] + nums[1] + nums[2]
        for i in range(ls - 2):
            j, k = i + 1, ls - 1
            while j < k:
                temp = sort_nums[i] + sort_nums[j] + sort_nums[k]
                if abs(target - temp) < abs(target - res):
                    res = temp
                if temp < target:
                    j += 1
                else:
                    k -= 1
        return res
```

### 18. 4Sum

[https://leetcode.com/problems/4sum/](https://leetcode.com/problems/4sum/)

#### Description

Given an array `nums` of _n_ integers and an integer `target`, are there elements _a_, _b_, _c_, and _d_ in `nums` such that _a_ + _b_ + _c_ + _d_ = `target`? Find all unique quadruplets in the array which gives the sum of `target`.

**Note:**

The solution set must not contain duplicate quadruplets.

**Example:**

```text
Given array nums = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```

#### Solution

[https://leetcode.com/problems/4sum/solution/](https://leetcode.com/problems/4sum/solution/)

```python
class Solution(object):
    def fourSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        d = {}
        nums.sort()

        output = []

        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                start = j+1
                end = len(nums)-1

                while start<end:
                    key = (nums[i], nums[j], nums[start], nums[end])
                    sum_= sum(key)

                    if target == sum_:
                        d[key] = True
                        start += 1
                        end -= 1

                    if target < sum_:
                        end -= 1
                    elif target > sum_:
                        start += 1


        return d.keys()
```

### 454. 4Sum II

[https://leetcode.com/problems/4sum-ii/](https://leetcode.com/problems/4sum-ii/)

#### Description

Given four lists A, B, C, D of integer values, compute how many tuples `(i, j, k, l)` there are such that `A[i] + B[j] + C[k] + D[l]` is zero.

To make problem a bit easier, all A, B, C, D have same length of N where 0 ≤ N ≤ 500. All integers are in the range of -228 to 228 - 1 and the result is guaranteed to be at most 231 - 1.

**Example:**

```text
Input:
A = [ 1, 2]
B = [-2,-1]
C = [-1, 2]
D = [ 0, 2]

Output:
2

Explanation:
The two tuples are:
1. (0, 0, 0, 1) -> A[0] + B[0] + C[0] + D[1] = 1 + (-2) + (-1) + 2 = 0
2. (1, 1, 0, 0) -> A[1] + B[1] + C[0] + D[0] = 2 + (-1) + (-1) + 0 = 0
```

#### Solution

[https://leetcode.com/problems/4sum-ii/discuss/93917/Easy-2-lines-O\(N2\)-Python](https://leetcode.com/problems/4sum-ii/discuss/93917/Easy-2-lines-O%28N2%29-Python)

```python
class Solution:
    def fourSumCount(self, A: List[int], B: List[int], C: List[int], D: List[int]) -> int:
        AB = collections.Counter(a+b for a in A for b in B)
        return sum(AB[-c-d] for c in C for d in D)
```

### REFERENCES

* [https://cs.stackexchange.com/questions/2973/generalised-3sum-k-sum-problem](https://cs.stackexchange.com/questions/2973/generalised-3sum-k-sum-problem)

