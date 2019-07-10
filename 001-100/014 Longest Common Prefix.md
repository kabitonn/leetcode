# [14. Longest Common Prefix](https://leetcode-cn.com/problems/longest-common-prefix/)

## 1. 题目描述(简单)

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:
```
Input: ["flower","flow","flight"]
Output: "fl"
```
Example 2:
```
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```
**Note:**
> All given inputs are in lowercase letters a-z

## 2. 思路

## 3. 解决方法

### 3.1 垂直比较



```java
    public String longestCommonPrefix(String[] strs) {
    	if(strs == null ||strs.length == 0)
    		return "";
    	int min = Integer.MAX_VALUE;
    	for (String str : strs)
    		min = Math.min(min, str.length());
        char c;
        int i=0;
        for(;i<min;i++) {
        	c = strs[0].charAt(i);
        	for(int j=1;j<strs.length;j++) {
        		if(strs[j].charAt(i)!=c) {
        			return strs[0].substring(0, i);
        		}
        	}
        }
        return strs[0].substring(0, i);
    }
```


### 3.2 水平比较




### 3.3 递归



```java
    public String longestCommonPrefix(String[] strs, int left, int right) {
    	if(left == right)
    		return strs[left];
    	int mid = (left+right)/2;
    	String lcpleft = longestCommonPrefix(strs, left, mid);
    	String lcpright = longestCommonPrefix(strs, mid+1, right);
    	String lcp = commonPrefix(lcpleft,  lcpright);
    	return lcp;
    }
    public String commonPrefix(String leftStr, String rightStr) {
    	int min = Math.min(leftStr.length(), rightStr.length());
    	for(int i=0;i<min;i++) {
    		if(leftStr.charAt(i)!=rightStr.charAt(i)) {
    			return leftStr.substring(0, i);
    		}
    	}
		return leftStr.substring(0,min);
	}
```






