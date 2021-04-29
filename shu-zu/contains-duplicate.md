# Contains Duplicate



### 217. Contains Duplicate\[E\]

[https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

#### Description

Given an array of integers, find if the array contains any duplicates.

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

**Example 1:**

```text
Input: [1,2,3,1]
Output: true
```

**Example 2:**

```text
Input: [1,2,3,4]
Output: false
```

**Example 3:**

```text
Input: [1,1,1,3,3,4,3,2,4,2]
Output: true
```

#### Solution

[https://leetcode.com/problems/contains-duplicate/solution/](https://leetcode.com/problems/contains-duplicate/solution/)

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(set(nums)) != len(nums)
```

### 219. Contains Duplicate II\[E\]

[https://leetcode.com/problems/contains-duplicate-ii/](https://leetcode.com/problems/contains-duplicate-ii/)

#### Description

Given an array of integers and an integer _k_, find out whether there are two distinct indices _i_ and _j_ in the array such that **nums\[i\] = nums\[j\]** and the **absolute** difference between _i_ and _j_ is at most _k_.

**Example 1:**

```text
Input: nums = [1,2,3,1], k = 3
Output: true
```

**Example 2:**

```text
Input: nums = [1,0,1,1], k = 1
Output: true
```

**Example 3:**

```text
Input: nums = [1,2,3,1,2,3], k = 2
Output: false
```

#### Solution

```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        by = {}
        for i, v in enumerate(nums):
            if v not in by:
                by[v] = [i]
            else:
                ii = by[v][-1]
                if i - ii <= k:
                    return True
                else:
                    by[v].append(i)
        return False
```

### 220. Contains Duplicate III\[M\]

[https://leetcode.com/problems/contains-duplicate-iii/](https://leetcode.com/problems/contains-duplicate-iii/)

#### Description

Given an array of integers, find out whether there are two distinct indices _i_ and _j_ in the array such that the **absolute** difference between **nums\[i\]** and **nums\[j\]** is at most _t_ and the **absolute** difference between _i_ and _j_ is at most _k_.

**Example 1:**

```text
Input: nums = [1,2,3,1], k = 3, t = 0
Output: true
```

**Example 2:**

```text
Input: nums = [1,0,1,1], k = 1, t = 2
Output: true
```

**Example 3:**

```text
Input: nums = [1,5,9,1,5,9], k = 2, t = 3
Output: false
```

#### Solution

```python

```

