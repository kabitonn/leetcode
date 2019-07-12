## [219. Contains Duplicate II](https://leetcode-cn.com/problems/contains-duplicate-ii/)

## 1. 题目描述(简单)

Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k.

Example 1:
```
Input: nums = [1,2,3,1], k = 3
Output: true
```
Example 2:
```
Input: nums = [1,0,1,1], k = 1
Output: true
```
Example 3:
```
Input: nums = [1,2,3,1,2,3], k = 2
Output: false
```
## 2. 思路

## 3. 解决方法

### 3.1 遍历


```java
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        for(int i=0;i<nums.length;i++) {
            for(int j=i+1;j<=i+k&&j<nums.length;j++) {
                if(nums[i]==nums[j]) {return true;}
            }
        }
        return false;
    }
```


### 3.2 HashMap


```java
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        Map<Integer,Integer> map = new HashMap<>();
        for(int i=0;i<nums.length;i++) {
            if(map.containsKey(nums[i])&&(i-map.get(nums[i])<=k)){
                return true;
            }
            else {
                map.put(nums[i], i);
            }
        }
        return false;
    }
```

### 3.3 HashSet 滑动窗口


```java
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        Set<Integer> set = new HashSet<>();
        for(int i=0;i<nums.length;i++) {
            if(set.add(nums[i])) {
                if(set.size()>k) {
                    set.remove(nums[i-k]);
                }
            }
            else {
                return true;
            }
        }
        return false;
    }
```




