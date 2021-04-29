# HCF & GCD



```text
def gcd(x, y):
    if x > y:
        (x, y) = (y, x)
    for factor in range(x, 1, -1):
        if x % factor == 0 and y % factor == 0:
            return factor
    return 1


def lcm(x, y):
    return x * y // gcd(x, y)


print(gcd(15, 27))
print(lcm(15, 27))

def gcd(x, y):
    """求最大公约数"""
    (x, y) = (y, x) if x > y else (x, y)
    for factor in range(x, 0, -1):
        if x % factor == 0 and y % factor == 0:
            return factor


def lcm(x, y):
    """求最小公倍数"""
    return x * y // gcd(x, y)
```

```python
def hcf(x, y):
   """该函数返回两个数的最大公约数"""

   # 获取最小值
   if x > y:
       smaller = y
   else:
       smaller = x

   for i in range(1,smaller + 1):
       if((x % i == 0) and (y % i == 0)):
           hcf = i

   return hcf


# 用户输入两个数字
num1 = int(input("输入第一个数字: "))
num2 = int(input("输入第二个数字: "))

print( num1,"和", num2,"的最大公约数为", hcf(num1, num2))

def gcd(x, y): # very fast
   return x if y == 0 else gcd(y, x%y)

print(gcd(378, 5940))  # result: 54

def lcm(x, y): # very fast
    s = x*y
    while y: x, y = y, x%y
    return s//x
print(lcm(120, 123)) #result: 4920

x = int(input('请输入第一个数:'))
y = int(input('请输入第二个数:'))
for i in range(1,min(x,y) + 1):
    if (y % i == 0) & (x % i == 0):
        divisor = i
print(divisor)

# 最小公倍数
def lcm(a, b):
    if b > a:
        a, b = b, a     # a为最大值
    if a % b == 0:
        return a        # 判断a是否为最小公倍数
    mul = 2             # 最小公倍数为最大值的倍数
    while a*mul % b != 0:
        mul += 1
    return a*mul

while(True):
    a = int(input("Input 'a':"))
    b = int(input("Input 'b':"))
    print(lcm(a, b))
```

输入两个正整数，计算它们的最大公约数和最小公倍数。

```text
x = int(input('x = '))
y = int(input('y = '))
# 如果x大于y就交换x和y的值
if x > y:
    # 通过下面的操作将y的值赋给x, 将x的值赋给y
    x, y = y, x
# 从两个数中较的数开始做递减的循环
for factor in range(x, 0, -1):
    if x % factor == 0 and y % factor == 0:
        print('%d和%d的最大公约数是%d' % (x, y, factor))
        print('%d和%d的最小公倍数是%d' % (x, y, x * y // factor))
        break
```

