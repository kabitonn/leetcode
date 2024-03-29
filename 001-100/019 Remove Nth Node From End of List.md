## [19. Remove Nth Node From End of List](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)

## 1. 题目描述(中等)

Given a linked list, remove the n-th node from the end of list and return its head.

Example:
```
Given linked list: 1->2->3->4->5, and n = 2.
After removing the second node from the end, the linked list becomes 1->2->3->5.
```
**Note**:
> Given n will always be valid.

Follow up:

> Could you do this in one pass?

## 2. 思路

1. 前后指针遍历$$n+(l-n)*2 = 2l - n$$
    1. 单个指针遍历$$l+l-n = 2l - n$$
2. 一次遍历，存储结点


## 3. 解决方法

### 3.1 两次遍历



```java
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode start = new ListNode(0);
        start.next = head;
    	ListNode last = start;
        int num = 0;
    	while(num++<n) {
    		last = last.next;
    	}
    	ListNode first = start;
    	while(last.next!=null) {
    		last = last.next;
    		first = first.next;
    	}
    	first.next = first.next.next;
    	return start.next;
    }
```



```java
    public ListNode removeNthFromEnd1(ListNode head, int n) {
        ListNode start = new ListNode(0);
        start.next = head;
    	ListNode first = start;
    	int len = 0;
        while(first.next!=null) {
    		first = first.next;
    		len++;
    	}
    	len-=n;
    	first = start;
    	while(len-->0) {
    		first = first.next;
    	}
    	first.next = first.next.next;
    	return start.next;
    }
```

### 3.2 一次遍历



```java
    public ListNode removeNthFromEnd2(ListNode head, int n) {
        ListNode start = new ListNode(0);
        start.next = head;
    	ListNode first = start;
    	List<ListNode> list = new ArrayList<>();
    	int len = 0;
        while(first.next!=null) {
        	list.add(first);
    		first = first.next;
    		len++;
    	}
    	len-=n;
    	first = list.get(len);
    	first.next = first.next.next;
    	return start.next;
    }
```





