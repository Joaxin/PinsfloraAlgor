# Sqrt



### 求根

首先我们需要定义一个floatrange：

```python
def floatrange(start,stop,steps):
    ''' Computes a range of floating value.

        Input:
            start (float)  : Start value.
            end   (float)  : End value
            steps (integer): Number of values

        Output:
            A list of floats

        Example:
            floatrange(0.25, 1.3, 5)
            [0.25, 0.5125, 0.775, 1.0375, 1.3]
    '''


    return [start + float(i) * (stop-start)/(float(steps)-1) for i in range(steps)]
floatrange(0.25, 1.3, 5)
```

```python
def F(n):
    return n * n - 2

def frange(start, stop, steps):
    return [start + i*steps for i in range(int((stop - start) / steps))]


N = 0.0001
for i in frange(1, 100, N):
    if F(i)*F(i+N) <= 0:
        print(i)
        break
# 1.4142000000000001
```

