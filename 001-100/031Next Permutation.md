## [31. Next Permutation](https://leetcode-cn.com/problems/next-permutation/)

## 1. 题目描述\(中等\)

Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order \(ie, sorted in ascending order\).

The replacement must be in-place and use only constant extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.

```
1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1
```

## 2. 思路

## 3. 解决方法

### 3.1

```java
    public void nextPermutation(int[] nums) {
        int index1 = -1;
        int index2 = -1;
        int len = nums.length;
        for(int i=0;i<len-1;i++) {
            for(int j=i+1;j<len;j++) {
                if(nums[i]<nums[j]) {
                    index1=i;
                    index2=j;
                }
            }
        }
        if(index1==-1)
            reverse(nums, 0);
        else {
            swap(nums, index1, index2);
            reverse(nums, index1+1);
        }
    }
    public void swap(int[] nums,int i,int j) {
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
    public void reverse(int[] nums,int i) {
        int j = nums.length-1;
        while(i<j) {
            swap(nums, i, j);
            i++;
            j--;
        }
    }
```

### 3.2

```java
    public void nextPermutation(int[] nums) {
    	int i = nums.length-2;
    	while(i>=0&&nums[i+1]<=nums[i]) {
    		i--;
    	}
    	if(i<0) {
    		reverse(nums, 0);
    		return;
    	}
    	int j = i+1;
    	while(j<nums.length&&nums[j]>nums[i]) {
    		j++;
    	}
    	j--;
    	swap(nums, i, j);
    	reverse(nums, i+1);
    }
    public void swap(int[] nums,int i,int j) {
    	int tmp = nums[i];
		nums[i] = nums[j];
		nums[j] = tmp;
    }
    public void reverse(int[] nums,int i) {
    	int j = nums.length-1;
    	while(i<j) {
    		swap(nums, i, j);
    		i++;
    		j--;
    	}
    }
```





