# 年份日期星期计算



一年有365天,有8760小时,有525600分钟,有31536000秒或者有366天,有874小时,有527040分钟,有316222400秒。

一年中，1、3、5、7、8、10、12月，为31天，4、6、9、11月，为30天。2月份平年为28天，闰年为29天。

**一个月**

31天：44640分钟,有2678400秒

30天：43200分钟,有2592000秒

29天：41760分钟,有2505600秒

地球围绕太阳公转一周，为一年。有两个周期，一个是恒星年，即365日6时9分10秒，另一个是太阳直射点在南北回归线之间来回移动而形成的回归年，即365日5时48分46秒。

> 公元，即公历纪年法，是一种源自于西方社会的纪年方法。原称基督纪元，又称西历或西元，是由意大利医生兼哲学家Aloysius Lilius对儒略历加以改革而制成的一种历法——《格里历》，其渊源为《授时历》。1582年，时任罗马教皇的格列高利十三世予以批准颁行。
>
> 公历纪年以耶稣诞生之年作为纪年的开始。在儒略历与格里高利历中，在耶稣诞生之后的日期，称为主的年份Anno Domini（A.D.）（拉丁）。而在耶稣诞生之前，称为主前Before Christ（B.C.）。
>
> 但是现代学者为了淡化其宗教色彩以及避免非基督徒的反感而多半改称用“公元”（Common era，缩写为C.E.）与“公元前”（Before the Common Era，缩写为 B.C.E.）的说法。

### 判断闰年

首先我们来简单的判断一下某年是不是闰年，目前使用的格里高利历闰年规则如下：

1. 公元年分非4的倍数，为平年
2. 公元年分为4的倍数但非100的倍数，为闰年
3. 公元年分为100的倍数但非400的倍数，为平年
4. 公元年分为400的倍数为闰年。

算法也很简单：

```python
year = int(input("输入一个年份: "))
if (year % 4) == 0:
   if (year % 100) == 0:
       if (year % 400) == 0:
           print("{0} 是闰年".format(year))   ## 公元年分为400的倍数为闰年
       else:
           print("{0} 不是闰年".format(year))
   else:
       print("{0} 是闰年".format(year))       ## 公元年分为4的倍数但非100的倍数，为闰年
else:
   print("{0} 不是闰年".format(year))
```

用函数简单判断如下：

```python
def is_leap_year(year):
    return year % 4 == 0 and year % 100 != 0 or year % 400 == 0
```

### 判断星期

已知公元元年1月1日为星期六，2000年1月1日为星期六

> 参考：教皇格里戈八世在1582年2月24日颁布法令，永远抹去了1582年10月5日到1582年10月14日。历史上从来不曾有过这10天（当时的旧历法已经和地球公转到春分点的实际时间相差十天，此时颁行了新历法格里历，数字上跳过了这十天来修正日期差错。比如：手机上的华为日历这几天也不存在）。
>
> 1582年10月4日是星期四，它的第二天是1582年10月15日星期五\(当时中国为大明万历十年秋\)。
>
> 因此考虑到这10天的影响再去推算，公元元年1月1日为星期六

我们需要先判断某年某月有几天，然后判断那天的星期。

或者你也可以作弊使用datetime模块：

```python
from datetime import date
date(1582, 10, 4).weekday()
0 ## 星期一
```

```python
# month_days = [
#     [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31],
#     [31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
# ][is_leap_year(year)]

def  month_days(Year, Month):
    if Month in (1, 3, 5, 7,  8, 10, 12):
        return 31
    elif Month in (4, 6, 9, 11):
        return 30
    elif is_leap_year(Year):
        return 29
    else:
        return 28

def  year_days(Year):
    if is_leap_year(Year):
        return 366
    else:
        return 365
```

接下来，对于一个给定的年份和月，推算当时的星期, 因为1582年10月4日之前的星期并没有多大意义，所以我们这不考虑。

```python
weekdays = {1: "星期一", 2: "星期二", 3: "星期三",
            4: "星期四", 5: "星期五", 6: "星期六", 0: "星期日", }


def cacl_weekday(Year, Month, Day):
    ## 0为星期天 6为星期六
    Weekday = 6
    days = past_days =0
    for month in range(1, Month):
        past_days += month_days(Year, month)
    ## 距离1月1日的天数
    ## 起始日期月份的总天数减去起始天数 + 中间月份的总天数 + 所在月份的天数
    past_days = past_days + Day - 1

    if Year >= 2000:
        days = past_days
        for year in range(2000, Year):
            days += year_days(year)
        ## 过去的天数，当天不算
        ## 用天数除以7，根据余数顺推 或者直接天数加Weekday除以7可省去顺推的步骤
        Weekday = (Weekday + days) % 7
        print('距离2000年已过去%d天, 当年已过去%d天, %s' % (days, past_days, weekdays.get(Weekday)))
    else:
        for year in range(Year+1, 2000):
            days += year_days(year)

        ## 当年剩余的天数
        ## 倒推，比如星期二倒推10天是星期六(倒推3天或者顺推4天)，平年1天，润年2天
        ## 或者Weekday减去天数除以7可省去顺推的步骤
        days = year_days(Year) - past_days + days
        Weekday = (Weekday - days) % 7
        print('距离2000年还有%d天, 当年已过去%d天, %s' % (days, past_days, weekdays.get(Weekday)))


Y, M, D = [int(i) for i in input('请输入一个年月日，以空格隔开，如2008 8 8: ').strip().split()]
cacl_weekday(Y, M, D)
```

```text
请输入一个年月日，以空格隔开，如2008 8 8: 2033 5 30
距离2000年已过去12203天, 当年已过去149天, 星期一
请输入一个年月日，以空格隔开，如2008 8 8: 1582 10 15
距离2000年还有152384天, 当年已过去287天, 星期五
请输入一个年月日，以空格隔开，如2008 8 8: 1 1 1
距离2000年还有730119天, 当年已过去0天, 星期一
```

### Refs

* [维基百科 闰年](https://zh.wikipedia.org/wiki/闰年)
* 计算星期的其他方法：[蔡勒公式](https://baike.baidu.com/item/蔡勒公式/10491767)

