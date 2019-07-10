# [21. Merge Two Sorted Lists](https://leetcode-cn.com/problems/merge-two-sorted-lists/)

## 1. 题目描述(简单)

## 2. 思路

## 3. 解决方法

### 3.1

### 3.2 递归



```java
    public  ListNode mergeTwoLists(ListNode l1, ListNode l2) {
		if(l1==null) {
			return l2;
		}
		if(l2==null) {
			return l1;
		}
		if(l1.val<l2.val) {
			l1.next = mergeTwoLists(l1.next, l2);
			return l1;
		}
		else {
			l2.next = mergeTwoLists(l1, l2.next);
			return l2;
		}
	}
```



