## [303. Range Sum Query - Immutable](https://leetcode-cn.com/problems/range-sum-query-immutable/)

## 1. 题目描述\(简单\)

Given an integer array nums, find the sum of the elements between indices i and j \(i ≤ j\), inclusive.

Example:

```
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```

Note:

* You may assume that the array does not change.
* There are many calls to sumRange function.

## 2. 思路

## 3. 解决方法

### 3.1 暴力法

```java
public class NumArray {
    private int[] nums;
    public NumArray(int[] nums) {
        this.nums = nums;
    }

    public int sumRange(int i, int j) {
        int sum = 0;
        for(;i<=j&&i<nums.length;i++) {
            sum+=nums[i];
        }
        return sum;
    }
}
```

### 3.2 动态规划+缓存

```java
public class NumArray {
	private int[] sums;
	public NumArray(int[] nums) {
		this.sums = new int[nums.length+1];
		for(int i=0;i<nums.length;i++) {
			sums[i+1] = sums[i]+nums[i];
		}
	}
	public int sumRange(int i, int j) {
		return sums[j+1]-sums[i];
	}
    
    /*public int sumRange(int i, int j) {
    	int sum = 0;
        for(;i<=j&&i<nums.length;i++) {
        	sum+=nums[i];
        }
        return sum;
    }*/
}
```



