#### [4. Median of Two Sorted Arrays](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)

## 1. 题目描述\(困难\)

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O\(log \(m+n\)\).

You may assume nums1 and nums2 cannot be both empty.

Example 1:

> nums1 = \[1, 3\]
>
> nums2 = \[2\]
>
> The median is 2.0

Example 2:

> nums1 = \[1, 2\]
>
> nums2 = \[3, 4\]
>
> The median is \(2 + 3\)/2 = 2.5

## 2. 思路

## 3. 解决方法

### 3.1 暴力法-归并数组

归并两个有序数组，返回中位数

```java
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int m=nums1.length;
        int n=nums2.length;
        int i=0,j=0;
        int mid = (m+n)/2;
        int[] nums = new int[m+n];
        int k=0;

        boolean isEven = (m+n)%2==0?true:false;
        while((k<=mid)&&(i<m||j<n)) {
            while(i<m&&(j>=n||nums1[i]<nums2[j])) {
                nums[k++] = nums1[i++];
            }
            while(j<n&&(i>=m||nums1[i]>=nums2[j])) {
                nums[k++] = nums2[j++];
            }
        }
        if(isEven) {
            return (nums[mid-1]+nums[mid])/2.0;
        }
        else {
            return nums[mid];
        }
    }
```

### 3.2 暴力法-归并部分数组

```java
public double findMedianSortedArrays(int[] nums1, int[] nums2) {
		int m=nums1.length;
		int n=nums2.length;
		int pre=0,cur=0;
		int i=0,j=0;
		
		int mid = (m+n)/2;
		boolean isEven = (m+n)%2==0?true:false;
		for(int k=0;k<=mid;k++) {
			pre = cur;
			if(i<m&&(j>=n||nums1[i]<nums2[j])) {
				cur = nums1[i++];
			}
			else if(j<n&&(i>=m)||nums1[i]>=nums2[j]) {
				cur = nums2[j++];
			}
		}
		if(isEven) {
			return (pre+cur)/2.0;
		}
		else {
			return cur;
		}
		
	}
```



