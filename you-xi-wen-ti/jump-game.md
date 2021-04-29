# Jump Game



### 55. Jump Game\[M\]

[https://leetcode.com/problems/jump-game/](https://leetcode.com/problems/jump-game/)

#### Description

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

**Example 1:**

```text
Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

**Example 2:**

```text
Input: nums = [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.
```

**Constraints:**

* `1 <= nums.length <= 3 * 10^4`
* `0 <= nums[i][j] <= 10^5`

#### Solution

[https://leetcode.com/problems/jump-game/solution/](https://leetcode.com/problems/jump-game/solution/)

[https://leetcode.com/articles/jump-game/](https://leetcode.com/articles/jump-game/)

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        ll = len(nums)
        s = ll - 1
        for i in reversed(range(ll - 1)):
            if i + nums[i] >= s:
                s = i
        return not s
```

### 45. Jump Game II\[H\]

[https://leetcode.com/problems/jump-game-ii/](https://leetcode.com/problems/jump-game-ii/)

#### Description

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

**Example:**

```text
Input: [2,3,1,1,4]
Output: 2
Explanation: The minimum number of jumps to reach the last index is 2.
    Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

#### Solution

```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        if len(nums) <= 1:
            return 0
        end = 0 + nums[0]
        start = 0
        step = 1
        maxDis = 0 + nums[0]
        while end < len(nums) - 1:
            for i in range(start + 1, end + 1):
                maxDis = max(maxDis, nums[i] + i)
            start = end
            end = maxDis
            step += 1
        return step
```

