## [169. Majority Element](https://leetcode-cn.com/problems/majority-element/)

## 1. 题目描述(简单)

Given an array of size n, find the majority element. The majority element is the element that appears more than $$⌊ n/2 ⌋$$ times.

You may assume that the array is non-empty and the majority element always exist in the array.

Example 1:
```
Input: [3,2,3]
Output: 3
```
Example 2:
```
Input: [2,2,1,1,1,2,2]
Output: 2
```


## 2. 思路

## 3. 解决方法

### 3.1 排序中位数


```java
    public int majorityElement(int[] nums) {
    	Arrays.sort(nums);
        return nums[nums.length/2];
    }
```


### 3.2 哈希表


```java
    public int majorityElement1(int[] nums) {
    	Map<Integer, Integer> map = new HashMap<>();
    	for(int n :nums) {
    		int frequence = map.getOrDefault(n, 0);
    		map.put(n, frequence+1);
    		if(map.get(n)>nums.length/2) {
    			return n;
    		}
    	}
    	return -1;
    }
```

### 3.3 


```java
    public int majorityElement2(int[] nums) {
    	int candidate=nums[0],count=1,i=1;
        for(;i<nums.length;i++)
        {
            if(candidate==nums[i])
                count++;
            else if(--count==0)
                candidate=nums[i+1];
        }   
        return candidate;
	}
```



