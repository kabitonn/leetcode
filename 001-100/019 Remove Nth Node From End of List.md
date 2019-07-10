# [19. Remove Nth Node From End of List](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)

## 1. 题目描述

## 2. 思路

## 3. 解决方法

### 3.1 



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

### 3.2



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





