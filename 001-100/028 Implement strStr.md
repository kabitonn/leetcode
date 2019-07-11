## [28. Implement strStr\(\)](https://leetcode-cn.com/problems/implement-strstr/)

## 1. 题目描述\(简单\)

Implement strStr\(\).

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

Example 1:

```
Input: haystack = "hello", needle = "ll"
Output: 2
```

Example 2:

```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

## 2. 思路

## 3. 解决方法

### 3.1



```java
    public int strStr(String haystack, String needle) {
    	if(needle.length()==0)
    		return 0;
    	for(int i=0;i<haystack.length();i++) {
    		boolean isExist = true;
    		for(int j=0;j<needle.length();j++) {
    			if(i+j<haystack.length()) {
    				if(haystack.charAt(i+j)!=needle.charAt(j)) {
    					isExist = false;
    					break;
    				}
    			}
    			else {
    				isExist = false;
					break;
				}
    		}
    		if(isExist) {
    			return i;
    		}
    	}
		return -1;
    }
```

```java
    public int strStr(String haystack, String needle) {
    	char[] hayArr = haystack.toCharArray();
        char[] needArr = needle.toCharArray();
    	for(int i=0;;i++) {
    		for(int j=0;;j++) {
    			if(j==needArr.length)	return i;
    			if(i+j==hayArr.length)	return -1;
				if(hayArr[i+j]!=needArr[j])	break;
    		}
    	}
    }
```

### 3.2



