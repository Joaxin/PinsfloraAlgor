# 指针

### C

```c
#include <stdio.h>
int main(int argc, char const *argv[])
{
    int x = 1,y = 2;
    printf("%d %p\n",x,&x );
    printf("%d %p\n",y,&y);
    x = y; 
    printf("%d %p\n",x,&x );
    printf("%d %p\n",y,&y);
    x = 2,y = 1;
    printf("%d %p\n",x,&x );
    printf("%d %p\n",y,&y);
    return 0;
}
```

```text
1 0x7ffd505d96ec
2 0x7ffd505d96e8
2 0x7ffd505d96ec
2 0x7ffd505d96e8
2 0x7ffd505d96ec
1 0x7ffd505d96e8
```

### Python

```python
x = 1
y = 2
print(x,id(x))
print(y,id(y))
x = y
print(x,id(x))
print(y,id(y))
x = 2
y = 1
print(x,id(x))
print(y,id(y))
```

```text
1 94162481652192
2 94162481652224
2 94162481652224
2 94162481652224
2 94162481652224
1 94162481652192
```

```python
class Point:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __del__(self):
        class_name = self.__class__.__name__
        print(class_name, "销毁")


pt1 = Point()
pt2 = pt1
pt3 = pt1
print(id(pt1), id(pt2), id(pt3))
# 87170760 87170760 87170760
del pt1
del pt2
del pt3
# Point 销毁
```

