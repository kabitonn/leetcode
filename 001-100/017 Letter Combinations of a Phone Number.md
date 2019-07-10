# [17. Letter Combinations of a Phone Number](https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/)

## 1. 题目描述(中等)



## 2. 思路

## 3. 解决方法

### 3.1 



```java
    public List<String> letterCombinations(String digits) {
    	
        List<String> list = new ArrayList<>();
        if(digits.length()==0)
    		return list;
        Map<Character, String> map = new HashMap<>();
        map.put('2', "abc");
        map.put('3', "def");
        map.put('4', "ghi");
        map.put('5', "jkl");
        map.put('6', "mno");
        map.put('7', "pqrs");
        map.put('8', "tuv");
        map.put('9', "wxyz");
        list.add("");
        for(char ch:digits.toCharArray()) {
        	String s = map.get(ch);
        	List<String> tmpList = new ArrayList<>();
        	for(char c:s.toCharArray()) {
        		for(String str:list) {
        			tmpList.add(str+c);
        		}
        	}
        	list = tmpList;
        }
        return list;
    }
```



### 3.2 



```java

```




