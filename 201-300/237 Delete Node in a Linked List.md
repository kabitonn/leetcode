## [237. Delete Node in a Linked List](https://leetcode-cn.com/problems/delete-node-in-a-linked-list/)

## 1. 题目描述\(简单\)

Write a function to delete a node \(except the tail\) in a singly linked list, given only access to that node.

Given linked list -- head = \[4,5,1,9\], which looks like following:

![](/assets/201-300/237-problem-1.png)

**Example 1:**

```
Input: head = [4,5,1,9], node = 5
Output: [4,1,9]
Explanation: You are given the second node with value 5, the linked list should become 4 -> 1 -> 9 
             after calling your function.
```

**Example 2:**

```
Input: head = [4,5,1,9], node = 1
Output: [4,5,9]
Explanation: You are given the third node with value 1, the linked list should become 4 -> 5 -> 9 
             after calling your function.
```

**Note**:

* The linked list will have at least two elements.
* All of the nodes' values will be unique.
* The given node will not be the tail and it will always be a valid node of the linked list.
* Do not return anything from your function.

## 2. 思路

## 3. 解决方法

### 3.1 与下一个节点交换
因为我们知道要删除的节点不是列表的末尾，所以我们可以保证这种方法是可行的

```java 
    public void deleteNode(ListNode node) {
    	node.val = node.next.val;
        node.next = node.next.next;
    }
```





