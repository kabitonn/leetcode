## [367. Valid Perfect Square](https://leetcode-cn.com/problems/valid-perfect-square/)

## 1. 题目描述(简单)

Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note: Do not use any built-in library function such as sqrt.

Example 1:
```
Input: 16
Output: true
```
Example 2:
```
Input: 14
Output: false
```


## 2. 思路

## 3. 解决方法

### 3.1 二分

转换为浮点数判断大小

```java
	public boolean isPerfectSquare(int num) {
		if(num<=0) {return false;}
		int low = 1;
		int high = num;
		while(low<=high) {
			int mid = low+(high-low)/2;
			if(mid == num*1.0/mid){
				return true;
			}
			else if(mid > num*1.0/mid){
				high = mid-1;
			}
			else{
				low = mid+1;
			}
		}
		return false;
	}
```
### 3.2 二分求左边界
求出小于等于算术平方根的最大值，判断其平方

```java
    public boolean isPerfectSquare(int num) {
        if (num <= 0) {
            return false;
        }
        int left = 1;
        int right = num;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (mid >= num / mid) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left * left == num;
    }
```




### 3.3 内置函数

