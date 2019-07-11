## [33. Search in Rotated Sorted Array](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/)

## 1. 题目描述\(中等\)

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

\(i.e., \[0,1,2,4,5,6,7\] might become \[4,5,6,7,0,1,2\]\).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

Your algorithm's runtime complexity must be in the order of $$O(log n)$$.

Example 1:

```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

Example 2:

```
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```

## 2. 思路

## 3. 解决方法

### 3.1 遍历

```java
    public int search(int[] nums, int target) {
        for(int i=0;i<nums.length;i++) {
            if(nums[i]==target)
                return i;
        }
        return -1;
    }
```

### 3.2 两段二分

```java
    public int search(int[] nums, int target) {
        int low = 0;
        int high = nums.length-1;
        while(low<=high) {
            int mid = (low+high)/2;
            int num ;
            if((nums[mid]<nums[0])==(target<nums[0])) {
                num = nums[mid];
            }
            else {
                num = nums[0]>target?Integer.MIN_VALUE:Integer.MAX_VALUE;
            }
            if(num>target) {
                high = mid-1;
            }
            else if (num<target) {
                low = mid+1;
            }
            else {
                return mid;
            }
        }
        return -1;
    }
```

### 3.3 确认旋转点后二分



```java
	public int search(int[] nums, int target) {
		int bias = getBiasByMax(nums);
		int start = 0;
		int end = nums.length-1;
		while(start<=end) {
			int mid = (start+end)/2;
			int trueMid = (mid+bias)%nums.length;
			if(nums[trueMid] == target)
				return trueMid;
			else if(nums[trueMid] < target) {
				start = mid+1;
			}
			else if(nums[trueMid] > target){
				end = mid -1;
			}
		}
		return -1;
	}
	public int getBiasByMin(int[] nums) {
		int start = 0;
		int end = nums.length-1;
		while (start<end) {
			int mid = (start+end)/2;
			if(nums[mid]>nums[end]) {
				start = mid+1;
			}
			else {
				end = mid;
			}
		}
		return start;
	}
	public int getBiasByMax(int[] nums) {
		int start = 0;
		int end = nums.length-1;
		while (start<end) {
			int mid = (start+end+1)/2;
			if(nums[mid]>nums[start]) {
				start = mid;
			}
			else {
				end = mid-1;
			}
		}
		return end+1;
	}
```


