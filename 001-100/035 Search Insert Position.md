## [35. Search Insert Position](https://leetcode-cn.com/problems/search-insert-position/)

## 1. 题目描述\(简单\)

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Example 1:

```
Input: [1,3,5,6], 5
Output: 2
```

Example 2:

```
Input: [1,3,5,6], 2
Output: 1
```

Example 3:

```
Input: [1,3,5,6], 7
Output: 4
```

Example 4:

```
Input: [1,3,5,6], 0
Output: 0
```

## 2. 思路

1. 遍历
2. 二分查找

## 3. 解决方法

### 3.1 遍历

```java
    public int searchInsert(int[] nums, int target) {
        int i=0;
        for(;i<nums.length;i++) {
            if(nums[i]==target) {    return i;    }
            else if(nums[i]>target) {    return i;    }
        }
        return i;
    }
```

### 3.2 二分查找

```java
    public int searchInsert(int[] nums, int target) {
        int low = 0;
        int high = nums.length-1;
        while(low<high) {
            int mid = (low+high)/2;
            if(nums[mid]==target) {    high = mid;    }
            else if(nums[mid]<target) {    low = mid+1;}
            else if(nums[mid]>target) {    high = mid;    }
        }
        low = (nums[low]<target)?low+1:low;
        return low;
    }
```





