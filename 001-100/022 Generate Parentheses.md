# [22. Generate Parentheses](https://leetcode-cn.com/problems/generate-parentheses/)

## 1. 题目描述(中等)

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

```
For example, given n = 3, a solution set is:
```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```
## 2. 思路

## 3. 解决方法

### 3.1 暴力法-遍历判断



```java
    public List<String> generateParenthesis(int n) {
        List<String> list = new ArrayList<>();
        char[] str = new char[n*2];
        generate(str, 0, list);
        return list;
    }
    public void generate(char[] str,int index,List<String> list) {
    	if(index==str.length) {
    		if(isValid(str)) {
    			list.add(String.valueOf(str));
    		}
    	}
    	else {
			str[index]='(';
			generate(str, index+1, list);
			str[index]=')';
			generate(str, index+1, list);
		}
    }
    public boolean isValid(char[] str) {
    	int balance = 0;
    	for(char c:str) {
    		if(c=='(') {
    			balance++;
    		}
    		else {
    			balance--;
    			if(balance<0)
    				return false;
    		}
    	}
    	return balance==0?true:false;
    }
```




### 3.2 回溯



```java
    public List<String> generateParenthesis(int n) {
        List<String> list = new ArrayList<>();
        backtrack(list, "", 0, 0, n);
        return list;
    }
    public void backtrack(List<String> list,String str,int left,int right,int n) {
    	if(str.length()==n*2) {
    		list.add(str);
    		return;
    	}
    	if(left<n) {
    		backtrack(list, str+'(', left+1, right, n);
    	}
    	if(right<left) {
    		backtrack(list, str+')', left, right+1, n);
    	}
    }
```



