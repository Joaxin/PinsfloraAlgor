# Sudoku



### 36. Valid Sudoku\[M\]

[https://leetcode.com/problems/valid-sudoku/](https://leetcode.com/problems/valid-sudoku/)

#### Description

Determine if a 9x9 Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:

1. Each row must contain the digits `1-9` without repetition.
2. Each column must contain the digits `1-9` without repetition.
3. Each of the 9 `3x3` sub-boxes of the grid must contain the digits `1-9` without repetition.

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png) A partially filled sudoku which is valid.

The Sudoku board could be partially filled, where empty cells are filled with the character `'.'`.

**Example 1:**

```text
Input:
[
  ["5","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
Output: true
```

**Example 2:**

```text
Input:
[
  ["8","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
Output: false
Explanation: Same as Example 1, except with the 5 in the top left corner being 
    modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.
```

**Note:**

* A Sudoku board \(partially filled\) could be valid but is not necessarily solvable.
* Only the filled cells need to be validated according to the mentioned rules.
* The given board contain only digits `1-9` and the character `'.'`.
* The given board size is always `9x9`.

#### Solution

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        vset = [0] * 9
        hset = [0] * 9
        bset = [0] * 9
        for i in range(9):
            for j in range(9):
                curr = board[i][j]
                if curr != '.':
                    index = 1 << (ord(curr) - ord('0'))
                    if (hset[i] & index) > 0 or\
                                    (vset[j] & index) > 0 or\
                                    (bset[(i / 3) * 3 + j / 3] & index) > 0:
                        return False
                    hset[i] |= index
                    vset[j] |= index
                    bset[(i / 3) * 3 + j / 3] |= index
        return True
```

### 37. Sudoku Solver\[H\]

[https://leetcode.com/problems/sudoku-solver/](https://leetcode.com/problems/sudoku-solver/)

#### Description

Write a program to solve a Sudoku puzzle by filling the empty cells.

A sudoku solution must satisfy **all of the following rules**:

1. Each of the digits `1-9` must occur exactly once in each row.
2. Each of the digits `1-9` must occur exactly once in each column.
3. Each of the the digits `1-9` must occur exactly once in each of the 9 `3x3` sub-boxes of the grid.

Empty cells are indicated by the character `'.'`.

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png) A sudoku puzzle...

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Sudoku-by-L2G-20050714_solution.svg/250px-Sudoku-by-L2G-20050714_solution.svg.png) ...and its solution numbers marked in red.

**Note:**

* The given board contain only digits `1-9` and the character `'.'`.
* You may assume that the given Sudoku puzzle will have a single unique solution.
* The given board size is always `9x9`.

#### Solution

[https://leetcode.com/discuss/84831/java-backtracking-stack-20ms](https://leetcode.com/discuss/84831/java-backtracking-stack-20ms)

```python
class Solution:
    def solveSudoku(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        empty = []
        for i in range(9):
            for j in range(9):
                if board[i][j] == '.':
                    empty.append(9 * i + j)
        self.solve(board, empty)

    def solve(self, board, empty):
        if len(empty) == 0:
            return True
        first_value = empty[-1]
        row, col = first_value / 9, first_value % 9
        for k in range(1, 10):
            if self.is_safe(board, row, col, str(k)):
                board[row][col] = str(k)
                empty.pop()
                if self.solve(board, empty):
                    return True
                board[row][col] = '.'
                empty.append(first_value)
        return False

    def is_safe(self, board, row, col, ch):
        for k in range(9):
            if board[k][col] == ch:
                return False
            if board[row][k] == ch:
                return False
        start_row, start_col = 3 * (row / 3), 3 * (col / 3)
        for i in range(start_row, start_row + 3):
            for j in range(start_col, start_col + 3):
                if board[i][j] == ch:
                    return False
        return True
```

