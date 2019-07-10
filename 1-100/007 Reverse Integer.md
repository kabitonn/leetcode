#### [7. Reverse Integer](https://leetcode-cn.com/problems/reverse-integer/)

## 1. 题目描述

## 2. 思路

## 3. 解决方法

### 3.1 溢出预处理

```java
    public int reverse1(int x) {
        int reverse = 0;
        while(x!=0) {
            if (reverse > Integer.MAX_VALUE/10 ) return 0;
            if (reverse < Integer.MIN_VALUE/10 ) return 0;
            reverse = reverse*10+x%10;
            x/=10;
        }
        return reverse;

    }
```

时间复杂度：$$O(log_{10}(x))$$
空间复杂度：$$O(1)$$。

### 3.2 数据类型预防



```java
    public int reverse(int x) {
        long reverse = 0;
        while(x!=0) {
        	reverse = reverse*10+x%10;
        	x/=10;
        }
        if(reverse < Integer.MIN_VALUE||reverse > Integer.MAX_VALUE) {
        	return 0;
        }
        return (int)reverse;
        
    }
```


