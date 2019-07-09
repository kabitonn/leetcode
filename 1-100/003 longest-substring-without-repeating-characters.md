#### [3. Longest Substring Without Repeating Characters](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

## 1. 题目描述\(中等\)

Given a string, find the length of the longest substring without repeating characters.

Example 1:

> Input: "abcabcbb"
>
> Output: 3
>
> Explanation: The answer is "abc", with the length of 3.

Example 2:

> Input: "bbbbb"
>
> Output: 1
>
> Explanation: The answer is "b", with the length of 1.

Example 3:

> Input: "pwwkew"
>
> Output: 3
>
> Explanation: The answer is "wke", with the length of 3.

**Note** that the answer must be a substring, "pwke" is a subsequence and not a substring.

## 2. 思路

## 3. 解决方法

### 3.1 暴力法

依次判断以当前元素为首的无重复元素子串是否为最长子串，以i为首j为尾的子串是否为无重复元素子串，若为重复元素子串，循环i+1为首的子串；若为无重复元素子串，判断当前长度j-i+1与maxNum并修改。

```java
    public int lengthOfLongestSubstring(String s) {
        if(s.length()==0) {
            return 0;
        }
        int maxNum = 1;
        char[] str = s.toCharArray();
        for(int i=0;i<str.length;i++) {
            p:for(int j=i+1;j<str.length;j++) {
                for(int k=0;k<j-i;k++) {
                    if(str[j]==str[i+k]) {
                        break p;
                    }
                }
                if(j-i+1>maxNum) {
                    maxNum = j-i+1;
                }
            }
        }
        return maxNum;
    }
```

```java
    public int lengthOfLongestSubstring(String s) {
        int maxNum = 0;
        Set<Character> set = new HashSet<>();
        char[] str = s.toCharArray();
        int n = str.length;
        for(int i=0;i<n;i++) {
            set.add(str[i]);
            for(int j=i+1;j<n;j++) {
                if(!set.contains(str[j])) {
                    set.add(str[j]);
                }
                else {
                    break;
                }
            }
            maxNum = Math.max(maxNum,set.size());
            set.clear();
        }

```

### 3.2 双指针\(滑动窗口\)

### 3.3 优化滑动窗口



