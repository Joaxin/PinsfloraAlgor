# Container With Most Water



### 11. Container With Most Water\[M\]

[https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)

#### Description

Given _n_ non-negative integers _a1_, _a2_, ..., _an_ , where each represents a point at coordinate \(_i_, _ai_\). _n_ vertical lines are drawn such that the two endpoints of line _i_ is at \(_i_, _ai_\) and \(_i_, 0\). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

**Note:** You may not slant the container and _n_ is at least 2.

![img](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)

The above vertical lines are represented by array \[1,8,6,2,5,4,8,3,7\]. In this case, the max area of water \(blue section\) the container can contain is 49.

**Example:**

```text
Input: [1,8,6,2,5,4,8,3,7]
Output: 49
```

#### Solution

[https://leetcode.com/problems/container-with-most-water/solution/](https://leetcode.com/problems/container-with-most-water/solution/)

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        return haystack.index(needle) if needle in haystack else -1
```

### 42. Trapping Rain Water\[H\]

[https://leetcode.com/problems/trapping-rain-water/](https://leetcode.com/problems/trapping-rain-water/)

#### Description

Given _n_ non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

![img](https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png) The above elevation map is represented by array \[0,1,0,2,1,0,1,3,2,1,2,1\]. In this case, 6 units of rain water \(blue section\) are being trapped. **Thanks Marcos** for contributing this image!

**Example:**

```text
Input: [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
```

#### Solution

![img](https://i.loli.net/2018/10/18/5bc7f473efbdc.png)

[https://leetcode.com/problems/trapping-rain-water/solution/](https://leetcode.com/problems/trapping-rain-water/solution/)

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        if not height: return 0
        n = len(height)
        left, right = [0] * n, [0] * n

        temp = 0
        for i in range(n):     
            temp= max(temp,height[i])
            left[i] = temp

        temp = 0
        for i in range(n-1,-1,-1):
            temp = max(temp,height[i])
            right[i] = temp

        res = 0
        for i in range(n):             
            res+=min(left[i],right[i])-height[i]
        return res
```

