## [257. Binary Tree Paths](https://leetcode-cn.com/problems/binary-tree-paths/)

## 1. 题目描述(简单)

Given a binary tree, return all root-to-leaf paths.

Note: A leaf is a node with no children.

Example:
```
Input:

   1
 /   \
2     3
 \
  5

Output: ["1->2->5", "1->3"]

Explanation: All root-to-leaf paths are: 1->2->5, 1->3
```

## 2. 思路

## 3. 解决方法

### 3.1 递归


```java
public List<String> binaryTreePaths(TreeNode root) {
        List<String> result = new ArrayList<>();
        if(root==null) {return result;}
        String string = ""+root.val;
        binaryTreePath(root, result, string);
        
        return result;
    }
    public void binaryTreePath(TreeNode p,List<String> list,String str) {
		if(p.left==null&&p.right==null) {
			list.add(str);
		}
		if(p.left!=null){
			binaryTreePath(p.left, list, str+"->"+p.left.val);
		}
		if(p.right!=null) {
			binaryTreePath(p.right, list, str+"->"+p.right.val);
		}
	}
```


```java
	public List<String> binaryTreePaths(TreeNode root) {
		List<String> result = new ArrayList<>();
		if(root==null) {return result;}
		binaryTreePath1(root, result, "");

		return result;
	}
	public void binaryTreePath1(TreeNode p,List<String> list,String str) {
		if(p.left==null&&p.right==null) {
			list.add(str+p.val);
			return;
		}
		str += p.val;
		if(p.left!=null){
			binaryTreePath1(p.left, list, str+"->");
		}
		if(p.right!=null) {
			binaryTreePath1(p.right, list, str+"->");
		}
	}
```



```java
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        binaryTreePath2(root, result, "");

        return result;
    }

    public void binaryTreePath2(TreeNode p, List<String> list, String str) {
        if (p == null) {
            return;
        }
        str += p.val;
        if (p.left == null && p.right == null) {
            list.add(str);
        } else {
            binaryTreePath2(p.left, list, str + "->");
            binaryTreePath2(p.right, list, str + "->");
        }
    }
```





### 3.2

