# 打印三角形图案 - Asterisks Problem



### 223. Rectangle Area\[M\]

[https://leetcode.com/problems/rectangle-area/](https://leetcode.com/problems/rectangle-area/)

#### Description

Find the total area covered by two **rectilinear** rectangles in a **2D** plane.

Each rectangle is defined by its bottom left corner and top right corner as shown in the figure.

![Rectangle Area](https://assets.leetcode.com/uploads/2018/10/22/rectangle_area.png)

**Example:**

```text
Input: A = -3, B = 0, C = 3, D = 4, E = 0, F = -1, G = 9, H = 2
Output: 45
```

**Note:**

Assume that the total area is never beyond the maximum possible value of **int**.

#### Solution

```python
class Solution:
    def computeArea(self, A: int, B: int, C: int, D: int, E: int, F: int, G: int, H: int) -> int:
        result = (C - A) * (D - B) + (G - E) * (H - F)
        # no overlap
        if (C <= E or G <= A or H <= B or D <= F):
            return result
        # overlap length on x
        dx = min(C, G) - max(A, E)
        # overlap length on y
        dy = min(D, H) - max(B, F)
        return result - dx * dy
```

打印三角形图案

```python
row = int(input('请输入行数: '))
for i in range(row):
    for _ in range(i + 1):
        print('*', end='')
    print()
```

```text
*
**
***
****
*****
```

```python
for i in range(row):
    for j in range(row):
        if j < row - i - 1:
            print(' ', end='')
        else:
            print('*', end='')
    print()
```

```text
    *
   **
  ***
 ****
*****
```

```python
for i in range(row):
    for _ in range(row - i - 1):
        print(' ', end='')
    for _ in range(2 * i + 1):
        print('*', end='')
    print()
`
```

```text
    *
   ***
  *****
 *******
*********
```

