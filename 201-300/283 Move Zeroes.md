## [283. Move Zeroes](https://leetcode-cn.com/problems/move-zeroes/)

## 1. 题目描述\(简单\)

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Example:

```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

**Note:**

* You must do this in-place without making a copy of the array.
* Minimize the total number of operations.

## 2. 思路

## 3. 解决方法

### 3.1 暴力法

```java
    public void moveZeroes(int[] nums) {
        for (int i = 0; i < nums.length; i++) {
            if(nums[i]==0) {
                int pos = i;
                for(int j=i+1;j<nums.length;j++) {
                    if(nums[j]==0) {continue;}
                    swap(nums, pos, j);
                    pos = j;
                }
            }
        }
    }
    public void swap(int[] nums, int i, int j) {
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
```

### 3.2 只关注非0
只固定非0元素，末尾补0

```java
    public void moveZeroes1(int[] nums) {
        int pos = 0;
        for(int i=0;i<nums.length;i++) {
            if(nums[i]!=0) {
                nums[pos++] = nums[i];
            }
        }
        for(int i=pos;i<nums.length;i++) {
            nums[i] = 0;
        }
    }
```

### 3.3 遍历替换

- 慢指针（pos）之前的所有元素都是非零的。
- 当前指针和慢速指针之间的所有元素都是零。

```java
    public void moveZeroes2(int[] nums) {
        int pos = 0;
        for(int i=0;i<nums.length;i++) {
            if(nums[i]!=0) {
                swap(nums, pos++, i);
            }
        }
    }
    public void swap(int[] nums, int i, int j) {
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
```



