## [100. Same Tree](https://leetcode-cn.com/problems/same-tree/)

## 1. 题目描述(简单)

Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.

Example 1:
```
Input:     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

Output: true
```
Example 2:
```
Input:     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

Output: false
```
Example 3:
```
Input:     1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

Output: false
```


## 2. 思路

1.递归
2.迭代

## 3. 解决方法

### 3.1 递归


```java
	public boolean isSameTree(TreeNode p, TreeNode q) {
		if(p==null&&q==null) {return true;}
		else if(p==null||q==null) {return false;}
        if(p.val!=q.val) {return false;}
        else {return isSameTree(p.left, q.left)&&isSameTree(p.right, q.right);}
    }
```


### 3.2 迭代


