## [83. Remove Duplicates from Sorted List](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)

## 1. 题目描述(简单)

Given a sorted linked list, delete all duplicates such that each element appear only once.

Example 1:
```
Input: 1->1->2
Output: 1->2
```
Example 2:
```
Input: 1->1->2->3->3
Output: 1->2->3
```
## 2. 思路

## 3. 解决方法

### 3.1 迭代

找到一个，删除一个；相等的话就删除下一个节点，不相等就后移

```java
    public ListNode deleteDuplicates(ListNode head) {
        ListNode cur = head;
        while(cur!=null&&cur.next!=null) {
        	ListNode next = cur.next;
        	if(cur.val == next.val) {
        		cur.next = next.next;
        	}else {
				cur = cur.next;
			}
        }
        return head;
    }
```

### 3.2


```java
    public ListNode deleteDuplicates2(ListNode head) {
    	if (head == null) {return null;}
        if (head.next!=null && head.val == head.next.val) {
        	head.next = head.next.next;
        	head = deleteDuplicates2(head);
        }else {
			head.next = deleteDuplicates2(head.next);
		}
        return head;
    }
```




