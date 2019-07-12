## [53. Maximum Subarray](https://leetcode-cn.com/problems/maximum-subarray/)

## 1. 题目描述(简单)

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

Example:
```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```
Follow up:
> If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.


## 2. 思路

1. 动态规划

## 3. 解决方法

### 3.1



```java
	public int maxSubArray(int[] nums) {
        int len = nums.length;
        int[] maxSums = new int[len];
        maxSums[0] = nums[0];
        int maxSum = maxSums[0];
        for(int i=1;i<len;i++) {
        	if(maxSums[i-1]<0) {
        		maxSums[i] = nums[i];
        	}else {
				maxSums[i] = maxSums[i-1] + nums[i];
			}
        	if(maxSums[i]>maxSum) {	maxSum = maxSums[i];}
        }
        return maxSum;
    }
```


```java
	public int maxSubArray(int[] nums) {
        int sum=0;
        int maxSum = Integer.MIN_VALUE;
        for(int num:nums){
        	if(sum<0) {sum = num;}
        	else {sum+=num;}
            if(maxSum<sum){	maxSum=sum;}
        }
        return maxSum;
    }
```





### 3.2

