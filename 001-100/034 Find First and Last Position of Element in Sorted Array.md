## [34. Find First and Last Position of Element in Sorted Array](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

## 1. 题目描述\(中等\)

Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of $$O(log n)$$.

If the target is not found in the array, return \[-1, -1\].

Example 1:

```
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
```

Example 2:

```
Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
```

## 2. 思路

## 3. 解决方法

### 3.1 一般二分查找+前后遍历

```java
    public int[] searchRange(int[] nums, int target) {
        int position = binarySearch(nums, target);
        if(position!=-1) {
            int start = position;
            int end = position;
            while(start>0 && nums[start-1]==target) {start--;}
            while(end<nums.length-1 && nums[end+1]==target) {end++;}
            return new int[] {start,end};
        }
        return new int[]{-1,-1};
    }    
    public int binarySearch(int[] nums, int target) {
        int low = 0;
        int high = nums.length-1;
        while(low<=high) {
            int mid = (low+high)/2;
            if(nums[mid]==target) {    return mid;}
            else if (nums[mid]>target) {    high = mid - 1;}
            else if (nums[mid]<target) {    low = mid + 1;}
        }
        return -1;
    }
```

### 3.2 改进二分查找

```java
    public int[] searchRange(int[] nums, int target) {
        int left = binarySearchMin(nums, target);
        if(left!=-1) {
            int start = left;
            int end = start;
            while(end<nums.length-1 && nums[end+1]==target) {end++;}
            return new int[] {start,end};
        }
        return new int[]{-1,-1};
    }
    public int binarySearchMin(int[] nums, int target) {
        int low = 0;
        int high = nums.length-1;
        while(low<high) {
            int mid = (low+high)/2;
            if (nums[mid]<target) {    low = mid + 1;}
            else{    high = mid;}
        }
        low = (low<nums.length && nums[low]==target)?low:-1;
        return low;
    }
```



