## [371. Sum of Two Integers](https://leetcode-cn.com/problems/sum-of-two-integers/)

## 1. 题目描述\(简单\)

Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.

Example 1:

```
Input: a = 1, b = 2
Output: 3
```

Example 2:

```
Input: a = -2, b = 3
Output: 1
```

## 2. 思路

## 3. 解决方法

### 3.1 位运算

a ^ b 无进位的相加  
\(a & b\) 每一位的进位

```java
    public int getSum(int a, int b) {
        while(b != 0){
            int sum = a ^ b;    //按位加但不进位
            int carry = (a & b) << 1;   //按位与表示进位
            a = sum;
            b = carry;
        }
        return a;
    }
```

### 



