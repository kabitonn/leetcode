## [258. Add Digits](https://leetcode-cn.com/problems/add-digits/)

## 1. 题目描述(简单)

Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

**Example:**
```
Input: 38
Output: 2 
Explanation: The process is like: 3 + 8 = 11, 1 + 1 = 2. 
             Since 2 has only one digit, return it.
```
**Follow up:**
> 
Could you do it without any loop/recursion in O(1) runtime?

## 2. 思路

## 3. 解决方法

### 3.1 暴力法


```java
	public int addDigits(int num) {
		while(num/10!=0) {
			int sum = 0;
			while(num!=0) {
				sum+=num%10;
				num/=10;
			}
			num=sum;
		}
		return num;
	}
```




### 3.2 规律


```java
	public int addDigits(int num) {
		if(num>9)
		{
			num=num%9;
			if(num==0)
				return 9;
		}
		return num;
	}
```



