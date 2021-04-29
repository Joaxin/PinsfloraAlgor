---
description: Best Time to Buy and Sell Stock(121.122.123.188.)
---

# Best Time to Buy and Sell Stock



### 121. Best Time to Buy and Sell Stock\[E\]

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

#### Description

You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.

**Example 1:**

```text
Input: [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
             Not 7-1 = 6, as selling price needs to be larger than buying price.
```

**Example 2:**

```text
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

#### Solution

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock/solution/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/solution/)

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        low = 2 ** 64 - 1
        profit = 0

        for price in prices:
          low = min(low, price)
          profit = max(profit, price - low)

        return profit
```

#### Approach 1: Brute Force

We need to find out the maximum difference \(which will be the maximum profit\) between two numbers in the given array. Also, the second number \(selling price\) must be larger than the first one \(buying price\).

In formal terms, we need to find $$\max(\text{prices[j]} - \text{prices[i]})$$, for every _i_ and _j_ such that _j_ &gt; _i_.

```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    maxprofit = 0;
    for (i = 0; i < prices.length - 1; i++) {
        for (j = i + 1; j < prices.length; j++) {
            profit = prices[j] - prices[i];
            if (profit > maxprofit)
                maxprofit = profit;
        }
    }
    return maxprofit;
};
```

**Complexity Analysis**

* Time complexity : $$O(n^2)$$. Loop runs $$\dfrac{n (n-1)}{2}$$ times.
* Space complexity : $$O(1)$$ Only two variables $$\text{maxprofit}$$ and $$\text{profit}$$ are used.

#### Approach 2: One Pass

> [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/solution/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/solution/)

The points of interest are the peaks and valleys. We need to find the largest peak following the smallest valley. We can maintain two variables - minprice and maxprofit corresponding to the smallest valley and maximum profit \(maximum difference between selling price and minprice\) obtained so far respectively.

```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    minprice = Number.MAX_VALUE;
    maxprofit = 0;
    for (i = 0; i < prices.length; i++) {
        if (prices[i] < minprice)
            minprice = prices[i];
        else if (prices[i] - minprice > maxprofit)
            maxprofit = prices[i] - minprice;
    }
    return maxprofit;
};
```

* Time complexity : O\(n\). Only a single pass is needed.
* Space complexity : O\(1\). Only two variables are used.

### 122. Best Time to Buy and Sell Stock II\[E\]

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

#### Description

Say you have an array `prices` for which the _i_th element is the price of a given stock on day _i_.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like \(i.e., buy one and sell one share of the stock multiple times\).

**Note:** You may not engage in multiple transactions at the same time \(i.e., you must sell the stock before you buy again\).

**Example 1:**

```text
Input: [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
             Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
```

**Example 2:**

```text
Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying again.
```

**Example 3:**

```text
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

**Constraints:**

* `1 <= prices.length <= 3 * 10 ^ 4`
* `0 <= prices[i] <= 10 ^ 4`

#### Solution

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/solution/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/solution/)

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        return sum([y - x for x, y in zip(prices[0:-1], prices[1:]) if x < y])
```

### 123. Best Time to Buy and Sell Stock III\[H\]

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)

#### Description

Say you have an array for which the _i_th element is the price of a given stock on day _i_.

Design an algorithm to find the maximum profit. You may complete at most _two_ transactions.

**Note:** You may not engage in multiple transactions at the same time \(i.e., you must sell the stock before you buy again\).

**Example 1:**

```text
Input: [3,3,5,0,0,3,1,4]
Output: 6
Explanation: Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
             Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.
```

**Example 2:**

```text
Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying again.
```

**Example 3:**

```text
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

#### Solution

[https://discuss.leetcode.com/topic/50360/python-dp-and-non-dp-solution](https://discuss.leetcode.com/topic/50360/python-dp-and-non-dp-solution)

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        ls = len(prices)
        if ls == 0:
            return 0
        b1 = b2 = -prices[0]
        s1 = s2 = 0
        for i in range(1, ls):
            s2 = max(s2, b2 + prices[i])
            b2 = max(b2, s1 - prices[i])
            s1 = max(b1 + prices[i], s1)
            b1 = max(b1, -prices[i])
        return max(s1, s2)
```

### 188. Best Time to Buy and Sell Stock IV\[H\]

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)

#### Description

Say you have an array for which the _i-_th element is the price of a given stock on day _i_.

Design an algorithm to find the maximum profit. You may complete at most **k** transactions.

**Note:** You may not engage in multiple transactions at the same time \(ie, you must sell the stock before you buy again\).

**Example 1:**

```text
Input: [2,4,1], k = 2
Output: 2
Explanation: Buy on day 1 (price = 2) and sell on day 2 (price = 4), profit = 4-2 = 2.
```

**Example 2:**

```text
Input: [3,2,6,5,0,3], k = 2
Output: 7
Explanation: Buy on day 2 (price = 2) and sell on day 3 (price = 6), profit = 6-2 = 4.
             Then buy on day 5 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
```

#### Solution

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/solution/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/solution/)

```python

```

### 309. Best Time to Buy and Sell Stock with Cooldown\[E\]

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)

#### Description

You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

Find the maximum profit you can achieve. You may complete as many transactions as you like \(i.e., buy one and sell one share of the stock multiple times\) with the following restrictions:

* After you sell your stock, you cannot buy stock on the next day \(i.e., cooldown one day\).

**Note:** You may not engage in multiple transactions simultaneously \(i.e., you must sell the stock before you buy again\).

**Example 1:**

```text
Input: prices = [1,2,3,0,2]
Output: 3
Explanation: transactions = [buy, sell, cooldown, buy, sell]
```

**Example 2:**

```text
Input: prices = [1]
Output: 0
```

**Constraints:**

* `1 <= prices.length <= 5000`
* `0 <= prices[i] <= 1000`

#### Solution

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/solution/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/solution/)

```python

```

