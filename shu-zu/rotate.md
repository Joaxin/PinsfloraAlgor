# Rotate



### 48. Rotate Image\[M\]

[https://leetcode.com/problems/rotate-image/](https://leetcode.com/problems/rotate-image/)

#### Description

ou are given an _n_ x _n_ 2D matrix representing an image.

Rotate the image by 90 degrees \(clockwise\).

**Note:**

You have to rotate the image [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm), which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.

**Example 1:**

```text
Given input matrix = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],

rotate the input matrix in-place such that it becomes:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]
```

**Example 2:**

```text
Given input matrix =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], 

rotate the input matrix in-place such that it becomes:
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]
```

#### Solution

```python

```

### 81. Search in Rotated Sorted Array II\[M\]

[https://leetcode.com/problems/search-in-rotated-sorted-array-ii/](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

#### Description

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

\(i.e., `[0,0,1,2,2,5,6]` might become `[2,5,6,0,0,1,2]`\).

You are given a target value to search. If found in the array return `true`, otherwise return `false`.

**Example 1:**

```text
Input: nums = [2,5,6,0,0,1,2], target = 0
Output: true
```

**Example 2:**

```text
Input: nums = [2,5,6,0,0,1,2], target = 3
Output: false
```

**Follow up:**

* This is a follow up problem to [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/description/), where `nums` may contain duplicates.
* Would this affect the run-time complexity? How and why?

#### Solution

### 154. Find Minimum in Rotated Sorted Array II\[H\]

[https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)

#### Description

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

\(i.e., `[0,1,2,4,5,6,7]` might become `[4,5,6,7,0,1,2]`\).

Find the minimum element.

The array may contain duplicates.

**Example 1:**

```text
Input: [1,3,5]
Output: 1
```

**Example 2:**

```text
Input: [2,2,2,0,1]
Output: 0
```

**Note:**

* This is a follow up problem to [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/).
* Would allow duplicates affect the run-time complexity? How and why?

#### Solution

```python

```

### 733. Flood Fill\[E\]

[https://leetcode.com/problems/flood-fill/](https://leetcode.com/problems/flood-fill/)

#### Description

An `image` is represented by a 2-D array of integers, each integer representing the pixel value of the image \(from 0 to 65535\).

Given a coordinate `(sr, sc)` representing the starting pixel \(row and column\) of the flood fill, and a pixel value `newColor`, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels \(also with the same color as the starting pixel\), and so on. Replace the color of all of the aforementioned pixels with the newColor.

At the end, return the modified image.

**Example 1:**

```text
Input: 
image = [[1,1,1],[1,1,0],[1,0,1]]
sr = 1, sc = 1, newColor = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
Explanation: 
From the center of the image (with position (sr, sc) = (1, 1)), all pixels connected 
by a path of the same color as the starting pixel are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected
to the starting pixel.
```

**Note:**

The length of `image` and `image[0]` will be in the range `[1, 50]`.

The given starting pixel will satisfy `0 <= sr < image.length` and `0 <= sc < image[0].length`.

The value of each color in `image[i][j]` and `newColor` will be an integer in `[0, 65535]`.

#### Solution

[https://leetcode.com/problems/flood-fill/solution/](https://leetcode.com/problems/flood-fill/solution/)

```python

```

