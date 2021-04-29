# Range Sum Query



### 303. Range Sum Query - Immutable\[E\]

[https://leetcode.com/problems/combination-sum/](https://leetcode.com/problems/combination-sum/)

#### Description

Given an integer array _nums_, find the sum of the elements between indices _i_ and _j_ \(_i_ ≤ _j_\), inclusive.

**Example:**

```text
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```

**Note:**

1. You may assume that the array does not change.
2. There are many calls to _sumRange_ function.

#### Solution

[https://leetcode.com/problems/range-sum-query-immutable/solution/](https://leetcode.com/problems/range-sum-query-immutable/solution/)

```python

```

### 304. Range Sum Query 2D - Immutable\[M\]

[https://leetcode.com/problems/range-sum-query-2d-immutable/](https://leetcode.com/problems/range-sum-query-2d-immutable/)

#### Description

Given a 2D matrix _matrix_, find the sum of the elements inside the rectangle defined by its upper left corner \(_row_1, _col_1\) and lower right corner \(_row_2, _col_2\).

![Range Sum Query 2D](https://leetcode.com/static/images/courses/range_sum_query_2d.png) The above rectangle \(with the red border\) is defined by \(row1, col1\) = **\(2, 1\)** and \(row2, col2\) = **\(4, 3\)**, which contains sum = **8**.

**Example:**

```text
Given matrix = [
  [3, 0, 1, 4, 2],
  [5, 6, 3, 2, 1],
  [1, 2, 0, 1, 5],
  [4, 1, 0, 1, 7],
  [1, 0, 3, 0, 5]
]

sumRegion(2, 1, 4, 3) -> 8
sumRegion(1, 1, 2, 2) -> 11
sumRegion(1, 2, 2, 4) -> 12
```

**Note:**

1. You may assume that the matrix does not change.
2. There are many calls to _sumRegion_ function.
3. You may assume that _row_1 ≤ _row_2 and _col_1 ≤ _col_2.

#### Solution

```python

```

### 307. Range Sum Query - Mutable\[M\]

[https://leetcode.com/problems/range-sum-query-mutable/](https://leetcode.com/problems/range-sum-query-mutable/)

#### Description

Given an integer array _nums_, find the sum of the elements between indices _i_ and _j_ \(_i_ ≤ _j_\), inclusive.

The _update\(i, val\)_ function modifies _nums_ by updating the element at index _i_ to _val_.

**Example:**

```text
Given nums = [1, 3, 5]

sumRange(0, 2) -> 9
update(1, 2)
sumRange(0, 2) -> 8
```

**Constraints:**

* The array is only modifiable by the _update_ function.
* You may assume the number of calls to _update_ and _sumRange_ function is distributed evenly.
* `0 <= i <= j <= nums.length - 1`

#### Solution

```python

```

