## [326. Power of Three](https://leetcode-cn.com/problems/power-of-three/)

## 1. 题目描述(简单)

Given an integer, write a function to determine if it is a power of three.

Example 1:
```
Input: 27
Output: true
```
Example 2:
```
Input: 0
Output: false
```
Example 3:
```
Input: 9
Output: true
```
Example 4:
```
Input: 45
Output: false
```
**Follow up:**
> Could you do it without using any loop / recursion?


## 2. 思路

## 3. 解决方法

### 3.1 暴力法


```java
	public boolean isPowerOfThree(int n) {
		if(n<=0) {return false;}
		while(n%3==0) {
			n/=3;
		}
		return n==1;
	}
```
时间复杂度：$$O(\log_b(n))$$，在我们的例子中是$$ O(\log n)$$。除数是用对数表示的。
空间复杂度：$$O(1)$$，没有使用额外的空间。


### 3.2 公式法

$$n = 3^i $$
$$ i = log_{3}(n) = \cfrac{log_b(n)}{log_b(3)}$$
```java
	public boolean isPowerOfThree1(int n) {
		//double r = Math.log10(n)/Math.log10(3);
		//return r==(int)r;
		return (Math.log10(n) / Math.log10(3)) % 1 == 0;
	}
```
时间复杂度：Unknown。这里主要消耗时间的运算是 Math.log，它限制了我们算法的时间复杂性。实现依赖于我们使用的语言和编译器 。
空间复杂度：$$O(1)$$


### 3.3 整数限制


