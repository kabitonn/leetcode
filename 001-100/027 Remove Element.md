# [27. Remove Element](https://leetcode-cn.com/problems/remove-element/)

## 1. 题目描述(简单)

## 2. 思路

## 3. 解决方法

### 3.1 



```java
    public int removeElement(int[] nums, int val) {
        int len = 0;
        for(int i=0;i<nums.length;i++) {
        	if(nums[i]!=val) {
        		nums[len++] = nums[i];
        	}
        }
        return len;
    }
```



### 3.2 



```java
    public int removeElement(int[] nums, int val) {
        int len = nums.length;
        int i=0;
        while(i<len) {
        	if(nums[i]==val) {
        		nums[i] = nums[--len];
        	}
        	else {
        		i++;
        	}
        }
        return len;
    }
```

