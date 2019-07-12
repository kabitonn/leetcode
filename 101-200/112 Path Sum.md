## [112. Path Sum](https://leetcode-cn.com/problems/path-sum/)

## 1. 题目描述(简单)

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

**Note**: A leaf is a node with no children.

Example:
```
Given the below binary tree and sum = 22,

      5
     / \
    4   8
   /   / \
  11  13  4
 /  \      \
7    2      1
return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.
```


## 2. 思路

1. 递归
2. 迭代

## 3. 解决方法

### 3.1 递归DFS


```java
    public boolean hasPathSum(TreeNode p, int sum) {
        if(p==null) {return false;}
        if(p.left==null&&p.right==null&&sum==p.val) {return true;}
        else {
			return hasPathSum(p.left, sum-p.val)||hasPathSum(p.right, sum-p.val);
		}
    }
```



### 3.2 迭代DFS


```java
    public boolean hasPathSum(TreeNode root, int sum) {
        if(root==null) {return false;}
        Deque<TreeNode> stack = new LinkedList<>();
        Deque<Integer> leftSumStack = new LinkedList<>();
        stack.push(root);
        leftSumStack.push(sum);
        while(!stack.isEmpty()) {
        	TreeNode pNode = stack.pop();
        	int leftSum = leftSumStack.pop();
        	if(pNode.left==null&&pNode.right==null&&leftSum==pNode.val) {
        		return true;
        	}
        	if(pNode.left!=null) {
        		stack.push(pNode.left);
        		leftSumStack.push(leftSum-pNode.val);
        	}
        	if(pNode.right!=null) {
        		stack.push(pNode.right);
        		leftSumStack.push(leftSum-pNode.val);
        	}
        }
        return false;
    }
```

