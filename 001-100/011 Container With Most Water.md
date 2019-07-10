# [11. Container With Most Water](https://leetcode-cn.com/problems/container-with-most-water/)

## 1. 题目描述\(中等\)

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate \(i, ai\). n vertical lines are drawn such that the two endpoints of line i is at \(i, ai\) and \(i, 0\). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

> **Note**: You may not slant the container and n is at least 2.

![](/assets/001-100/011-problem-1.png)

The above vertical lines are represented by array \[1,8,6,2,5,4,8,3,7\]. In this case, the max area of water \(blue section\) the container can contain is 49.

Example:

```
Input: [1,8,6,2,5,4,8,3,7]
Output: 49
```

## 2. 思路

## 3. 解决方法

### 3.1 暴力法-遍历



```java
    public int maxArea(int[] height) {
    	int maxArea = 0;
    	int area;
    	for(int i=0;i<height.length-1;i++) {
    		for(int j=i+1;j<height.length;j++) {
    			area = (j-i)*Math.min(height[i], height[j]);
    			if(area>maxArea) {
    				maxArea = area;
    			}
    		}
    	}
        return maxArea;
    }

```

### 3.2 双指针



```java
    public int maxArea(int[] height) {
    	int left = 0, right = height.length-1;
    	int maxArea = 0;
    	while(left<right) {
    		maxArea=Math.max(maxArea, (right-left)*Math.min(height[left], height[right]));
    		if(height[left]<height[right]) {
    			left++;
    		}
    		else {
				right--;
			}
    	}
    	return maxArea;
    }

```







