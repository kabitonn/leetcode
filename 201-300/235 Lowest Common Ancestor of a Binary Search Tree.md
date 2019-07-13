## [235. Lowest Common Ancestor of a Binary Search Tree](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

## 1. 题目描述\(简单\)

Given a binary search tree \(BST\), find the lowest common ancestor \(LCA\) of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants \(where we **allow a node to be a descendant of itself**\).”

Given binary search tree:  root = \[6,2,8,0,4,7,9,null,null,3,5\]

![](/assets/201-300/235-problem-1.png)

Example 1:

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
Output: 6
Explanation: The LCA of nodes 2 and 8 is 6.
```

Example 2:

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
Output: 2
Explanation: The LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.
```

**Note**:

* All of the nodes' values will be unique.
* p and q are different and both values will exist in the BST.

## 2. 思路

1. 递归
2. 迭代

## 3. 解决方法

### 3.1 递归


```java
	public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
		if(root==null||p==null||q==null) {return null;}
		if(p.val<root.val&&q.val<root.val) {
			return lowestCommonAncestor(root.left, p, q);
		}
		else if (p.val>root.val&&q.val>root.val) {
			return lowestCommonAncestor(root.right, p, q);
		}
		else  {
			return root;
		}
	}
```


### 3.2 迭代


```java
	public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
		if(root==null||p==null||q==null) {return null;}
		int pVal = p.val;
		int qVal = q.val;
		TreeNode node = root;
		while(node!=null) {
			int val = node.val;
			if(pVal<val&&qVal<val) {
				node = node.left;
			}
			else if (pVal>val&&qVal>val) {
				node = node.right;
			}
			else {
				return node;
			}
		}
		return null;
	}
```




