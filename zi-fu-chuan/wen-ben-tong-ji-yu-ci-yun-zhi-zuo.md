# 文本统计与词云制作

### Text Analyzer

`characterCount.py`

其中的

```python
if c in dic:
    dic[c]+=1
else: 
    dic[c]=1
```

我们也可以用`dic[c] = dic.get(c, 0)+ 1` 或者

```python
dic.setdefault(c, 0)
ic[c] = dic[c] + 1
```

代替。

```python
filename = input("Enter a filename: ")
with open(filename) as f:
  text = f.read()

dic = {}
l = len(text)
for c in text.lower():
    if c == "\n":
       c="\n"
    if c ==" ":
       c=" "
    if c in dic:
       dic[c]+=1
    else: 
       dic[c]=1

letters = dict(sorted(dic.items(), key = lambda item:item[1], reverse = True))

for c in letters:
    print ("{0} - {1} - {2}%".format(c if c in "abcdefghijklmnopqrstuvwxyz" else repr(c), letters[c], round(100 * letters[c] / l,4)))
```

```python
Enter a filename: emma.txt
' ' - 147632 - 16.6426%
e - 86021 - 9.6972%
t - 59201 - 6.6738%
a - 54379 - 6.1302%
o - 53199 - 5.9971%
n - 47288 - 5.3308%
i - 46606 - 5.2539%
h - 42568 - 4.7987%
s - 42508 - 4.7919%
r - 40914 - 4.6123%
d - 28582 - 3.2221%
l - 27674 - 3.1197%
m - 20705 - 2.3341%
u - 20646 - 2.3274%
'\n' - 16830 - 1.8973%
w - 16290 - 1.8364%
y - 15706 - 1.7705%
c - 15462 - 1.743%
f - 15140 - 1.7067%
...
```

### Pig Latin

“Pig Latin”是一个英语儿童文字改写游戏，整个游戏遵从下述规则：

\(1\). 元音字母是‘a’、‘e’、‘i’、‘o’、‘u’。字母‘y’在不是第一个字母的情况下，也被视作元音字母。其他字母均为辅音字母。例如，单词“yearly”有三个元音字母（分别为‘e’、‘a’和最后一个‘y’）和三个辅音字母（第一个‘y’、‘r’和‘l’）。

\(2\). 如果英文单词以元音字母开始，则在单词末尾加入“hay”后得到“Pig Latin”对应单词。

例如，“ask”变为“askhay”，“use”变为“usehay”。

\(3\). 如果英文单词以‘q’字母开始，并且后面有个字母‘u’，将“qu”移动到单词末尾加入“ay”后得到“Pig Latin”对应单词。例如，“quiet”变为“ietquay”，“quay”变为“ayquay”。

\(4\). 如果英文单词以辅音字母开始，所有连续的辅音字母一起移动到单词末尾加入“ay”后

得到“Pig Latin”对应单词。例如，“tomato”变为“omatotay”， “school” 变为“oolschay”，“you” 变为“ouyay”，“my” 变为“ymay ”，“ssssh” 变为“sssshay”。

\(5\). 如果英文单词中有大写字母，必须所有字母均转换为小写。

输入样例Welcome to the Python world Are you ready

输出样例elcomeway otay ethay ythonpay orldway arehay ouyay eadyray

```python
def Pig_Latin(string):
    string = string.lower()
    if string[0] in 'aeiou':
        string += 'hay'
    elif string[0:2] == 'qu':
        string = string[2:] + 'quay'
    else:
        i = 0
        for c in string:
            if c in 'aeiouy':
                break
            else:
                i += 1
        string = string[i:] + string[0:i] + 'ay'
    return string

text = 'Python is intended to be a highly readable language \
It is designed to have an uncluttered visual layout frequently using English key\
words where other languages use punctuation Furthermore Python has a smaller\
number of syntactic exceptions and special cases than C or Pascal'
sstring = text.split()
for s in sstring:
    print(Pig_Latin(s))
```

[https://stackoverflow.com/questions/1155617/count-the-number-occurrences-of-a-character-in-a-string](https://stackoverflow.com/questions/1155617/count-the-number-occurrences-of-a-character-in-a-string)

