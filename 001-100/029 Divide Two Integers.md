## [29. Divide Two Integers](https://leetcode-cn.com/problems/divide-two-integers/)

## 1. 题目描述\(中等\)

Given two integers dividend and divisor, divide two integers without using multiplication, division and mod operator.  
Return the quotient after dividing dividend by divisor.  
The integer division should truncate toward zero.

Example 1:

```
Input: dividend = 10, divisor = 3
Output: 3
```

Example 2:

```
Input: dividend = 7, divisor = -3
Output: -2
```

**Note:**

> * Both dividend and divisor will be 32-bit signed integers.
> * The divisor will never be 0.
> * Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range:$$ [−2^{31},  2^{31} − 1]$$. For the purpose of this problem, assume that your function returns $$2^{31} − 1$$when the division result overflows.

## 2. 思路

采用负数存储，避免最大负数转为正数溢出

1. 递归：每次求得除数最大的二次幂乘积，二次幂作为结果的累积，相减后剩余部分递归求解
2. 迭代：除数逐渐指数递增，若即将溢出，归为初始值，除数的倍数作为结果的累积
   ## 3. 解决方法

### 3.1 递归

```java
    public int divide(int dividend, int divisor) {
        if (dividend == Integer.MIN_VALUE && divisor == -1) {
            return Integer.MAX_VALUE;
        }
        // 全部记录为负数，统一符号，同时避免最大负数转为正数时会溢出的问题
        int negativetiveDividend = dividend > 0 ? 0 - dividend : dividend;
        int negativeDivisor = divisor > 0 ? 0 - divisor : divisor;
        // 记录位运算左移次数
        int leftTime = 0;
        int result = 0;
        // 记录最小整数右移一位的结果
        int maxRight1 = Integer.MIN_VALUE >> 1;
        if (dividend == 0 || negativetiveDividend - negativeDivisor > 0) return 0;
        while (negativetiveDividend - negativeDivisor < 0) {
            // 如果除数小于最小整数右移一位，说明不能再左移了，跳出循环
            if (negativeDivisor < maxRight1 || negativetiveDividend - (negativeDivisor << 1) > 0) break;
            negativeDivisor = negativeDivisor << 1;
            leftTime ++;
        }
        // 递归
        result = (1 << leftTime) 
                + divide(negativetiveDividend - negativeDivisor, divisor > 0 ? 0 - divisor : divisor);
        if ((dividend^divisor)<0) {
            result = 0 - result;
        }
        return result;
    }
```

### 3.2 迭代

```java
    public int divide(int dividend, int divisor) {
        if (dividend == Integer.MIN_VALUE && divisor == -1) {
            return Integer.MAX_VALUE;
        }
        // 全部记录为负数，统一符号，同时避免最大负数转为正数时会溢出的问题
        int negativetiveDividend = dividend > 0 ? 0 - dividend : dividend;
        int negativeDivisor = divisor > 0 ? 0 - divisor : divisor;
        boolean negative= (dividend^ divisor)<0;
        if (dividend == 0 || negativetiveDividend - negativeDivisor > 0) return 0;
        int res = 0;
        int leftTime = 0;
        // 记录最小整数右移一位的结果
        int maxRight1 = Integer.MIN_VALUE >> 1;
        int curNegativetiveDividend = negativetiveDividend;
        int curNegativeDivisor = negativeDivisor;
        while (curNegativetiveDividend - curNegativeDivisor <= 0 && curNegativetiveDividend!=0) {
            curNegativetiveDividend -= curNegativeDivisor;
            res += (1<<leftTime);

            if (curNegativeDivisor < maxRight1 || curNegativetiveDividend - (curNegativeDivisor << 1) > 0) {
                curNegativeDivisor = negativeDivisor;
                leftTime = 0;
                continue;
            }
            curNegativeDivisor <<=1;
            leftTime ++;
        }
        return res = negative?-res:res;
    }
```



