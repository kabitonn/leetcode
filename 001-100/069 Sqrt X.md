## [69. Sqrt(x)](https://leetcode-cn.com/problems/sqrtx/)

## 1. 题目描述(简单)

Implement int sqrt(int x).

Compute and return the square root of x, where x is guaranteed to be a non-negative integer.

Since the return type is an integer, the decimal digits are truncated and only the integer part of the result is returned.

Example 1:
```
Input: 4
Output: 2
```
Example 2:
```
Input: 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since 
             the decimal part is truncated, 2 is returned.
```
## 2. 思路
1. 遍历
2. 二分
3. 牛顿法
## 3. 解决方法

### 3.1



### 3.2

### 3.3 

$$x_{k+1} = x_k - f(x_k)/f'(x_k)$$
$$f(x_n) = x^2 - n$$
$$x_{k+1} = x_k - (x_k^2 - n)/2x_k = (x_k^2 + n)/2x_k = (x_k + n/x_k)/2$$

```java
    public int mySqrt(int x) {
        long a = x;
        while (a * a > x) {
            a = (a + x / a) / 2;
        }
        return (int) a;
    }
```

