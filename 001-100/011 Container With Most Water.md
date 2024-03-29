## [11. Container With Most Water](https://leetcode-cn.com/problems/container-with-most-water/)

## 1. 题目描述\(中等\)

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate \(i, ai\). n vertical lines are drawn such that the two endpoints of line i is at \(i, ai\) and \(i, 0\). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

**Note**:

> You may not slant the container and n is at least 2.

![](/assets/001-100/011-problem-1.png)

The above vertical lines are represented by array \[1,8,6,2,5,4,8,3,7\]. In this case, the max area of water \(blue section\) the container can contain is 49.

Example:

```
Input: [1,8,6,2,5,4,8,3,7]
Output: 49
```

## 2. 思路

1. 直接遍历任意两根柱子求容量
2. 选定一根柱子，第二根若小于已遍历过的当前最大值，进行下次循环
3. 左右两个柱子，低的柱子向对端移动找到更高的才有可能在底边短的情况下容量更大；

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

时间复杂度：$$O(n^2)$$。

空间复杂度：$$O(1)$$。

### 3.2 暴力法改进

```java
    public int maxArea(int[] height) {
        int maxArea =0;
        int area;
        int max;
        for(int i=0;i<height.length-1;i++) {
            area = (height.length-1-i)*Math.min(height[i], height[height.length-1]);
            if(area>maxArea) {
                maxArea = area;
            }
            max = height[height.length-1];
            for(int j=height.length-1;j>i;j--) {
                if(height[j]<=max)
                    continue;
                max = height[j];
                area = (j-i)*Math.min(height[i], height[j]);
                if(area>maxArea) {
                    maxArea = area;
                }
            }
        }
        return maxArea;
    }
```

### 3.3 双指针

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

时间复杂度：$$O(n)$$。

空间复杂度：$$O(1)$$。

