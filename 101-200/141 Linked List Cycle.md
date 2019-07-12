## [141. Linked List Cycle](https://leetcode-cn.com/problems/linked-list-cycle/)

## 1. 题目描述\(简单\)

Given a linked list, determine if it has a cycle in it.

To represent a cycle in the given linked list, we use an integer pos which represents the position \(0-indexed\) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.

Example 1:

```
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

![](/assets/101-200/141-problem-1.png)

Example 2:

```
Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

![](/assets/101-200/141-problem-2.png)

Example 3:

```
Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.
```

![](/assets/101-200/141-problem-3.png)

Follow up:

> Can you solve it using O\(1\) \(i.e. constant\) memory?

## 2. 思路

## 3. 解决方法

### 3.1 快慢指针相交


```java
    public boolean hasCycle(ListNode head) {
    	if(head==null) {return false;}
        ListNode fast = head;
        ListNode slow = head;
        while(fast!=null&&fast.next!=null) {
        	slow = slow.next;
        	fast = fast.next.next;
        	if(slow == fast) {return true;}
        }
        return false;
    }
```

### 3.2 哈希集


```java
    public boolean hasCycle1(ListNode head) {
    	ListNode cur = head;
    	Set<ListNode> set = new HashSet<>();
    	while(cur!=null) {
    		if(set.contains(cur)) {return true;}
    		set.add(cur);
    		cur = cur.next;
    	}
    	return false;
    }
```




