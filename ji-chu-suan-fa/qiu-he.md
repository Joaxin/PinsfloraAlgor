# 求和

数学家高斯的故事。当高斯还是一个小孩时，老师想给全班同学布置很多计算作业。老师让他们从 0 加到 100。高斯想到了 一个聪明办法，在几秒钟内算出了答案，但你可以用 for 循环写一个 Python 程序，替你完成计算。

$$
计算 \displaystyle \sum \limits_{n=1}^{100}n = 1+2+3+4+5+6+\dots+100的和
$$

$$求和公式 \sum_{i=1}^{100} i = \frac{n(n+1)}{2}$$

#### While

`while`语句的代码：

```python
n = 1
total = 0
while n <= 100: 
    total = total + n
    n += 1
print(total)
```

```javascript
let n = 1
let total = 0
while (n <= 100) {
   total = total + n;
   n++;
}
console.log(total)
```

```javascript
let n = 1
let total = 0
do {  
   total = total + n;
   n++; 
}
while (n <= 100); 
console.log(total)
```

`break`关键词用于让执行提前跳出 `while`循环。如果执行遇到 `break`语句，就会马上退出 while 循环。

```python
n = 1
total = 0
while True:
    total = total + n
    n += 1
    if n > 100: 
        break 
print(total)
```

`continue`关键词用于让循环继续执行。如果程序执行遇到 `continue`语句，就会马上跳回到循环开始处，重新开始循环。

```python
n = 1
total = 0
while True:
    total = total + n
    n += 1
    if n <= 100: 
        continue
    else:
        break
print(total)
```

换一个顺序,`break`与`continue`同理，不作赘述。

```python
n = 1
total = 1
while n < 100:
    n += 1
    total = total + n
print(sum)
```

#### For

for 循环可以固定循环次数, 所以在知道循环执行的次数的情况下，会很方便。

```python
total = 0 
for n in range(101): 
    total = total + n
print(total)
```

```python
total = 0 
for n in range(100, 0, -1): ## 开始、停止和步长参数
    total = total + n
print(total)
```

```javascript
let total = 0 
for (let n=1; n <= 100; n++) {
    total = total + n
}
console.log(total)
```

然后的话，我们还可以用下面的代码来实现1~100之间的偶数求和。

```python
total = 0
for n in range(2, 101, 2):
    total += n
print(total)
```

也可以通过在循环中使用`if`分支结构的方式来实现相同的功能:

```python
total = 0
for n in range(1, 101):
    if n % 2 == 0:
        total += n
print(total)
```

也可以使用高阶函数reduce，

```python
from functools import reduce
l = range(1,101)
print(reduce(lambda x,y:x+y, l))
# 5050
```

