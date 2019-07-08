# 001. Two Sum

## 1. 题目描述（简单）

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution.

Example:

> ```java
> Given nums = [2, 7, 11, 15], target = 9,
> Because nums[0] + nums[1] = 2 + 7 = 9,
> return [0, 1].
> ```

## 2. 解决方法

### 2.1 暴力-双重循环

```
    public int[] twoSum(int[] nums, int target) {
        for(int i=0;i<nums.length;i++) {
        	for(int j=i+1;j<nums.length;j++) {
    			if ((nums[i]+nums[j]) == target) {
    				return new int[] {i,j};
        		}
        	}
        }
        return null;
    }
```



