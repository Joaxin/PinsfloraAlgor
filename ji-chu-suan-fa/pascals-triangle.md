# Pascal's Triangle



> [杨辉三角](https://zh.wikipedia.org/wiki/%E6%9D%A8%E8%BE%89%E4%B8%89%E8%A7%92%E5%BD%A2)

### 118. Pascal's Triangle\[E\]

[https://leetcode.com/problems/pascals-triangle/](https://leetcode.com/problems/pascals-triangle/)

#### Description

Given a non-negative integer _numRows_, generate the first _numRows_ of Pascal's triangle.

![img](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif) In Pascal's triangle, each number is the sum of the two numbers directly above it.

**Example:**

```text
Input: 5
Output:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

#### Solution

```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        pascal = list()
        L = [1]
        for t in range(numRows):
            LL = L[:]
            pascal.append(LL)
            L.append(0)
            L = [L[i - 1] + L[i] for i in range(len(L))]
        return pascal
```

[https://leetcode.com/problems/pascals-triangle/solution/](https://leetcode.com/problems/pascals-triangle/solution/)

### 119. Pascal's Triangle II\[E\]

[https://leetcode.com/problems/pascals-triangle-ii/](https://leetcode.com/problems/pascals-triangle-ii/)

#### Description

Given a non-negative index _k_ where _k_ ≤ 33, return the _k_th index row of the Pascal's triangle.

Note that the row index starts from 0.

![img](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif) In Pascal's triangle, each number is the sum of the two numbers directly above it.

**Example:**

```text
Input: 3
Output: [1,3,3,1]
```

**Follow up:**

Could you optimize your algorithm to use only _O_\(_k_\) extra space?

#### Solution

```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        pascal = list()
        L = [1]
        for t in range(rowIndex):
            L.append(0)
            L = [L[i - 1] + L[i] for i in range(len(L))]
        return L
```

```text
输入格式:
一个正整数 n

输出格式：
相应高度的帕斯卡三角形，两个数字之间有一个空格

输入样例：
6

输出样例：
     1
    1 1
   1 2 1
  1 3 3 1
 1 4 6 4 1
1 5 10 10 5 1


帕斯卡三角形，又称杨辉三角形是二项式系数在三角形中的一种几何排列。帕斯卡三角形通常从第0行开始枚举，并且每一行的数字是上一行相邻两个数字的和。在第0行只写一个数字1，然后构造下一行的元素。将上一行中数字左侧上方和右侧上方的数值相加。如果左侧上方或者右侧上方的数字不存在，用0替代。下面给出6行的帕斯卡三角形：
     1
    1 1
   1 2 1
  1 3 3 1
 1 4 6 4 1
1 5 10 10 5 1
编写程序，输入帕斯卡三角形的高度 n，然后生成和上面例子一样风格的三角形。

输入格式:
一个正整数 n

输出格式：
相应高度的帕斯卡三角形，两个数字之间有一个空格

输入样例：
6

输出样例：
     1
    1 1
   1 2 1
  1 3 3 1
 1 4 6 4 1
1 5 10 10 5 1
 # 帕斯卡三角形
```

```text
# -*- coding: utf-8 -*-
"""
Created on Mon Jun 22 19:17:30 2015

@author: Piiska
"""

mCache = {}
def pascalWithDict(n,k):
 if n==k or k==0 or n==1:
 return 1
 if k==1:
 return n
 if mCache.has_key((n,k)):
 return mCache[(n,k)]
else:
 mCache[n,k] = pascalWithDict(n-1,k-1)+pascalWithDict(n-1,k)
 return mCache[n,k]

## 获得每行pascal列表
def generatePascal(depth):
 lines = []
 for row in range(depth):
 line = []
 for col in range(row+1):
 line.append(pascal(row, col))
lines.append(line)
 return lines

if __name__ =="__main__":
 high = int(raw_input("pls enter the height of pascal:"))
 lines = generatePascal(high)
 for i in range(high):
 print lines[i]
```

```python
NUM =input()
def printLine(lineList):
    lineList = [str(temp) for temp in lineList]
    print("%s%s" % (" " * (NUM - len(lineList)), " ".join(lineList)))

for i in range(NUM):
    if i < 2:
        pascal = [1] * (i + 1)     
    else:
        pascal[1:-1] = [(temp + pascal[j]) for j, temp in enumerate(pascal[1:])]
    printLine(pascal)
```

The following code demonstrates how to implement a so-called Pascal's Triangle.

```python
def triangles():
    L = [1]
    while 1:
        yield L
        L.append(0)
        L = [L[i - 1] + L[i] for i in range(len(L))]
n = 0
for t in triangles():
    print(t)
    n = n + 1
    if n == 10:
        break
```

```python
[1]
[1, 1]
[1, 2, 1]
[1, 3, 3, 1]
[1, 4, 6, 4, 1]
[1, 5, 10, 10, 5, 1]
[1, 6, 15, 20, 15, 6, 1]
[1, 7, 21, 35, 35, 21, 7, 1]
[1, 8, 28, 56, 70, 56, 28, 8, 1]
[1, 9, 36, 84, 126, 126, 84, 36, 9, 1]
```

```python
# def subsetsWithDup(nums):
#     sub = [[]]
#     for i in nums:
#         for j in range(len(sub)):
#             sub.append(sub[j]+[i])
    # import itertools
    # sub.sort() 
    # return list(sub for sub,_ in itertools.groupby(sub))
    # return list(map(list,set(map(tuple, sub))))
    # return  [list(s) for s in (set([tuple(l) for l in sub]))]

# def subsetsWithDup(nums):
#     sub = [[]]
#     for i in nums:
#         for j in range(len(sub)):
#             sub.append(sorted(sub[j]+[i]))
#     sets = set([tuple(l) for l in sub[1:]])
#     return  sum([k[0] for k in sets])
# # 没顺序要求

# print(subsetsWithDup([3,1,2,4]))

def generate(numRows):
    def triangles():
        L = [1]
        while 1:
            yield L
            L.append(0)
            L = [L[i - 1] + L[i] for i in range(len(L))]
    n = 0
    pascal = list()
    for t in triangles():
        tt = t[:]
        pascal.append(tt)
        n = n + 1 
        if n == numRows:
            break
    return pascal

print(generate(6))
```

```python
num = int(input('Number of rows: '))
yh = [[]] * num
for row in range(len(yh)):
    yh[row] = [None] * (row + 1)
    for col in range(len(yh[row])):
        if col == 0 or col == row:
            yh[row][col] = 1
        else:
            yh[row][col] = yh[row - 1][col] + yh[row - 1][col - 1]
        print(yh[row][col], end=' ')
    print()
```

