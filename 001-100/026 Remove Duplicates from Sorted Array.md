## [26. Remove Duplicates from Sorted Array](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)

## 1. 题目描述\(简单\)

Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with $$O(1)$$ extra memory.

Example 1:

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```

Example 2:

```
Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.
```

## 2. 思路

1. 有序数组，和前者一样即为重复
2. 和每次第一个不重复的值比较，不一样对有效索引递增

## 3. 解决方法

### 3.1

```java
    public int removeDuplicates(int[] nums) {
        if(nums.length==0)
            return 0;
        int len = 0;
        for(int i=1;i<nums.length;i++) {
            if(nums[i]!=nums[i-1]) {
                nums[++len] = nums[i];
            }
        }
        return len+1;
    }
```

### 3.2

```java
    public int removeDuplicates(int[] nums) {
        if(nums.length==0)
            return 0;
        int len = 0;
        for(int i=1;i<nums.length;i++) {
            if(nums[i]!=nums[len]) {
                nums[++len] = nums[i];
            }
        }
        return len+1;
    }
```



