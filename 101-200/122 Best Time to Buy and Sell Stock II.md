## [122. Best Time to Buy and Sell Stock II](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/)

## 1. 题目描述\(简单\)

Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like \(i.e., buy one and sell one share of the stock multiple times\).

**Note**:

* You may not engage in multiple transactions at the same time \(i.e., you must sell the stock before you buy again\).

Example 1:

```
Input: [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
             Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
```

Example 2:

```
Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying again.
```

Example 3:

```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

## 2. 思路

## 3. 解决方法

### 3.1 一次遍历

![](/assets/101-200/122-solution-1-1.png)

如果第二个数字大于第一个数字，我们获得的总和将是最大利润

```java
    public int maxProfit(int[] prices) {
        int maxProfit = 0;
        for(int i=1;i<prices.length;i++) {
            if(prices[i]>=prices[i-1]) {
                maxProfit += prices[i] - prices[i-1];
            }
        }
        return maxProfit;
    }
```

时间复杂度：$$O(n)$$，遍历一次。  
空间复杂度：$$O(1)$$，需要常量的空间。

### 3.2 峰谷法

![](/assets/101-200/122-solution-2-1.png)

数学语言：  
$$TotalProfit = \sum_i(height(peak_i) - height(valley_i)) $$

```java
    public int maxProfit(int[] prices) {
        int maxProfit = 0;
        int len = prices.length;
        int i=0;
        while(i<len-1) {
            while(i<len-1&&prices[i]>=prices[i+1]) {i++;}
            int valley = prices[i];
            while(i<len-1&&prices[i]<=prices[i+1]) {i++;}
            int peak = prices[i++];
            maxProfit += (peak-valley);
        }

        return maxProfit;
    }
```

时间复杂度：$$O(n)$$，遍历一次。  
空间复杂度：$$O(1)$$，需要常量的空间。

