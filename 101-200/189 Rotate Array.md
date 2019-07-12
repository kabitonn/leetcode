## [189. Rotate Array](https://leetcode-cn.com/problems/rotate-array/)

## 1. 题目描述(简单)
Given an array, rotate the array to the right by k steps, where k is non-negative.

Example 1:
```
Input: [1,2,3,4,5,6,7] and k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```
Example 2:
```
Input: [-1,-100,3,99] and k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```
**Note**:
- Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.
- Could you do it in-place with O(1) extra space?



## 2. 思路

## 3. 解决方法

### 3.1 旋转k次


```java
    public void rotate(int[] nums, int k) {
        int len = nums.length;
        k%=len;
        if(len == 0||k==0) {return;}
    	for(int i=0;i<k;i++) {
        	int tmp = nums[len-1];
        	for(int j=len-1;j>0;j--) {
        		nums[j] = nums[j-1];
        	}
        	nums[0] = tmp;
        }
    }
```
时间复杂度：$$O(n*k)$$。每个元素都被移动 1 步$$O(n)$$ k次$$O(k)$$） 。
空间复杂度：$$O(1)$$ 。没有额外空间被使用。


### 3.2 三次反转

```java
   public void rotate(int[] nums, int k) {
    	int len = nums.length;
        k%=len;
        if(len == 0||k==0) {return;}
        reverse(nums, 0, len-1);
        reverse(nums, 0, k-1);
        reverse(nums, k, len-1);
    }
    public void reverse(int[] nums, int i,int j) {
    	while(i<j) {
		int tmp = nums[i];
		nums[i] = nums[j];
		nums[j] = tmp;
		i++;
		j--;
    	}
    }
```
### 3.3 环状替换


```java
    public void rotate(int[] nums,int k) {
        int len = nums.length;
        k%=len;
        if(len == 0||k==0) {return;}
        int count = 0;
        for (int start = 0; count < nums.length; start++) {
            int current = start;
            int prev = nums[start];
            do {
                current = (current + k) % nums.length;
                int temp = nums[current];
                nums[current] = prev;
                prev = temp;
                count++;
            } while (start != current);
        }
    }
```




