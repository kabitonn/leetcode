## [118. Pascal's Triangle](https://leetcode-cn.com/problems/pascals-triangle/)

## 1. 题目描述\(简单\)

Given a non-negative integer numRows, generate the first numRows of Pascal's triangle.

![](/assets/101-200/118-problem-1.png)

In Pascal's triangle, each number is the sum of the two numbers directly above it.

Example:

```
Input: 5
Output:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

## 2. 思路

## 3. 解决方法

### 3.1


```java 
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> lists = new ArrayList<>();
        if(numRows == 0) {return lists;}
        List<Integer> firstLine = new ArrayList<>();
        firstLine.add(1);
        lists.add(firstLine);
        for(int i=1;i<numRows;i++) {
        	List<Integer> preLine = lists.get(i-1);
        	List<Integer> line = new ArrayList<>();
        	line.add(1);
        	for(int j=1;j<i;j++) {
        		line.add(preLine.get(j-1)+preLine.get(j));
        	}
        	line.add(1);
        	lists.add(line);
        }
        return lists;
    }
```

### 3.2



