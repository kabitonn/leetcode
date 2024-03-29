## [136. Single Number](https://leetcode-cn.com/problems/single-number/)

## 1. 题目描述(简单)

Given a non-empty array of integers, every element appears twice except for one. Find that single one.

Note:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

Example 1:
```
Input: [2,2,1]
Output: 1
Example 2:

Input: [4,1,2,1,2]
Output: 4
```



## 2. 思路

1. 排序，前后相等即为重复
2. HashMap
3. 异或


## 3. 解决方法

### 3.1 排序


```java
    public int singleNumber(int[] nums) {
    	Arrays.sort(nums);
        for(int i=0;i<nums.length;i++) {
        	if(i+1<nums.length&&nums[i]==nums[i+1]) {
        		while(i+1<nums.length&&nums[i]==nums[i+1]) {i++;}
        	}
        	else {
				return nums[i];
			}
        }
        return 0;
    }
```


### 3.2 HashMap


```java
    public int singleNumber(int[] nums) {
    	Map<Integer, Integer> map = new HashMap<>();
    	for(int n:nums) {
    		Integer count = map.get(n);
    		count = count==null?1:count+1;
    		map.put(n, count);
    	}
    	for(Integer n:map.keySet()) {
    		if(map.get(n)==1) {
    			return n;
    		}
    	}
    	return 0;
    }
```


### 3.3 异或运算
- $$a⊕0 = a$$
- $$a⊕a = 0$$
- $$a⊕b⊕a=(a⊕a)⊕b=0⊕b=b$$


```java
    public int singleNumber(int[] nums) {
    	int xor = 0;
    	for(int n:nums) {
    		xor ^=  n;
    	}
    	return xor;
    }
```

