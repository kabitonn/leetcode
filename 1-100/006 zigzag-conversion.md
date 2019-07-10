#### [6. ZigZag Conversion](https://leetcode-cn.com/problems/zigzag-conversion/)

## 1. 题目描述\(中等\)

The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: \(you may want to display this pattern in a fixed font for better legibility\)

```
P   A   H   N

A P L S I I G

Y   I   R
```

And then read line by line: "PAHNAPLSIIGYIR"  
Write the code that will take a string and make this conversion given a number of rows:  
string convert\(string s, int numRows\);

Example 1:

> Input: s = "PAYPALISHIRING", numRows = 3  
> Output: "PAHNAPLSIIGYIR"

Example 2:

> Input: s = "PAYPALISHIRING", numRows = 4  
> Output: "PINALSIGYAHRPI"  
> Explanation:

```
P     I    N
A   L S  I G
Y A   H R
P     I
```

## 2. 思路

## 3. 解决方法

### 3.1 顺序写依次存入不同行

```java
    public String convert(String s, int numRows) {
        if(numRows==1)
            return s;
        int len = s.length();
        StringBuilder[] rows = new StringBuilder[numRows];
        for(int i=0;i<numRows;i++) {
            rows[i] = new StringBuilder();
        }
        int asc = -1;
        int cur_row = 0;
        for(int i=0;i<len;i++) {
            rows[cur_row].append(s.charAt(i));
            if(cur_row==0||cur_row==numRows-1) {
                asc=-asc;
            }
            cur_row+=asc;
        }
        StringBuilder stringBuilder = new StringBuilder();
        for(int i=0;i<numRows;i++) {
            stringBuilder.append(rows[i].toString());
        }
        return stringBuilder.toString();
    }
```

时间复杂度：$$O(n)$$，n 是字符串的长度。

空间复杂度：$$O(n)$$，保存每个字符需要的空间。

### 3.2 Z字形规律

找出按 Z 形排列后字符的规律，然后直接保存起来。


```java
    public String convert1(String s, int numRows) {
    	if(numRows==1)
    		return s;
    	int len = s.length();
    	int cycle = 2*numRows-2;
    	StringBuilder stringBuilder = new StringBuilder();
    	for(int i=0;i<numRows;i++) {
    		for(int j=0;j+i<len;j+=cycle) {
    			stringBuilder.append(s.charAt(j+i));
    			if(i!=0&&i!=numRows-1&&j+cycle-i<len) {
    				stringBuilder.append(s.charAt(j+cycle-i));
    			}
    		}
    	}
    	return stringBuilder.toString();
    }

```



