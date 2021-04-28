# 控制流

控制流的元素

[https://cloud.tencent.com/developer/article/1523672](https://cloud.tencent.com/developer/article/1523672)

### If

```text
if name == 'Mary': 
     print('Hello Mary') 
if password == 'swordfish': 
     print('Access granted.') 
else: 
     print('Wrong password.') 

 if name == 'Alice': 
    print('Hi, Alice.') 
else: 
    print('Hello, stranger.')
```

```python
if name == 'Alice': 
    print('Hi, Alice.') 
elif age < 12: 
    print('You are not Alice, kiddo.') 

elif age > 100: 
    print('You are not Alice, grannie.') 
elif age > 2000: 
    print('Unlike you, Alice is not an undead, immortal vampire.') 
次序




if name == 'Alice': 
    print('Hi, Alice.') 
elif age < 12: 
    print('You are not Alice, kiddo.') 
else: 
    print('You are neither Alice nor a little kid.')
```

```python
while True: 
    print('Who are you?') 
    name = input() 
    if name != 'Joe': 
        continue 
    print('Hello, Joe. What is the password? (It is a fish.)') 
    password = input() 
    if password == 'swordfish': 
        break 
print('Access granted.')
```

“类真”和“类假”的值 其他数据类型中的某些值，条件认为它们等价于 True 和 False。在用于条件 时，0、0.0 和' '（空字符串）被认为是 False，其他值被认为是 True。例如，请看 下面的程序：

```python
name = '' 
while not name:
    print('Enter your name:') 
    name = input() 
print('How many guests will you have?') 
numOfGuests = int(input()) 
if numOfGuests:
    print('Be sure to have enough room for all your guests.')
print('Done')
```

如果用户输入一个空字符串给 name，那么 while 语句的条件就会是 True ， 程序继续要求输入名字。如果 numOfGuests 不是 0 ，那么条件就被认为是 True， 程序就会为用户打印一条提醒信息。 可以用 not name != ' '代替 not name，用 numOfGuests != 0 代替 numOfGuests， 但使用类真和类假的值会让代码更容易阅读。

```python
import random

def getAnswer(answerNumber):
    if answerNumber == 1:
        return 'It is certain'
    elif answerNumber == 2:
        return 'It is decidely decidedly so'
    elif answerNumber == 3:
        return 'Yes'
    elif answerNumber == 4:
        return 'Reply hazy try again'
    elif answerNumber == 5:
        return 'Ask again later'
    elif answerNumber == 6:
        return 'Concentrate and ask again'
    elif answerNumber == 7:
        return 'My reply is no'
    elif answerNumber == 8:
        return 'Outlook not so good'
    elif answerNumber == 9:
        return 'Very doubtful'

r = random.randint(1, 9)
fortune = getAnswer(r)
print(fortune)
# print(getAnswer(random.randint(1, 9)))
```

```text
import random

messages = ['It is certain',
    'It is decidedly so',
    'Yes definitely',
    'Reply hazy try again',
    'Ask again later',
    'Concentrate and ask again',
    'My reply is no',
    'Outlook not so good',
    'Very doubtful']

print(messages[random.randint(0, len(messages) - 1)])
```

过神奇 8 球程序。利用列表，可以写出更优雅的版本。

```text
allGuests = {'Alice': {'apples': 5, 'pretzels': 12}, 
             'Bob': {'ham sandwiches': 3, 'apples': 2}, 
             'Carol': {'cups': 3, 'apple pies': 1}} 

def totalBrought(guests, item): 
    numBrought = 0 
     for k, v in guests.items(): 
         numBrought = numBrought + v.get(item, 0) 
    return numBrought 

print('Number of things being brought:') 
print(' - Apples ' + str(totalBrought(allGuests, 'apples'))) 
print(' - Cups ' + str(totalBrought(allGuests, 'cups'))) 
print(' - Cakes ' + str(totalBrought(allGuests, 'cakes'))) 
print(' - Ham Sandwiches ' + str(totalBrought(allGuests, 'ham sandwiches'))) 
print(' - Apple Pies ' + str(totalBrought(allGuests, 'apple pies')))
```

factorial

```text
n = int(input('n = '))
result = 1
for x in range(1, n + 1):
    result *= x
print('%d! = %d' % (n, result))
```

