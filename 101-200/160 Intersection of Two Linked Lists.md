## [160. Intersection of Two Linked Lists](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/)

## 1. 题目描述\(简单\)

Write a program to find the node at which the intersection of two singly linked lists begins.

For example, the following two linked lists:

![](/assets/101-200/160-problem-1.png)

begin to intersect at node c1.

Example 1:

![](/assets/101-200/160-problem-2.png)
```
Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3  
Output: Reference of the node with value = 8  
Input Explanation: The intersected node's value is 8 (note that this must not be 0 if the two lists intersect). 
                   From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,0,1,8,4,5]. 
                   There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.
```
Example 2:

![](/assets/101-200/160-problem-3.png)

```
Input: intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
Output: Reference of the node with value = 2
Input Explanation: The intersected node's value is 2 (note that this must not be 0 if the two lists intersect). 
                   From the head of A, it reads as [0,9,1,2,4]. From the head of B, it reads as [3,2,4]. 
                   There are 3 nodes before the intersected node in A; There are 1 node before the intersected node in B.
```

Example 3:

![](/assets/101-200/160-problem-4.png)

```
Input: intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
Output: null
Input Explanation: From the head of A, it reads as [2,6,4]. From the head of B, it reads as [1,5]. 
                   Since the two lists do not intersect, intersectVal must be 0, 
                   while skipA and skipB can be arbitrary values.
Explanation: The two lists do not intersect, so return null.
```

**Notes**:

* If the two linked lists have no intersection at all, return null.
* The linked lists must retain their original structure after the function returns.
* You may assume there are no cycles anywhere in the entire linked structure.
* Your code should preferably run in O\(n\) time and use only O\(1\) memory.

## 2. 思路

## 3. 解决方法

### 3.1


```java
	public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
		ListNode pA = headA;
		ListNode pB = headB;
		int lenA = 0;
		int lenB = 0;
		while(pA!=null) {
			lenA++;
			pA = pA.next;
		}
		while(pB!=null) {
			lenB++;
			pB = pB.next;
		}
		int diff = lenA - lenB;
		if(diff>0) {
			while(diff--!=0) {
				headA = headA.next;
			}
		}
		else if (diff<0) {
			while(diff++!=0) {
				headB = headB.next;
			}
		}
		while(headA!=null) {
			if(headA==headB) {return headA;}
			headA = headA.next;
			headB = headB.next;
		}
		return null;
	}
```


### 3.2


```java
	public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
		if(headA==null||headB==null) {return null;}
		ListNode pA = headA;
		ListNode pB = headB;
		while(pA!=pB) {
			pA = pA==null?headB:pA.next;
			pB = pB==null?headA:pB.next;
		}
		return pA;
	}
```

### 3.3 构造环求入口点



```java
	public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
		if (headA == null || headB == null) {	return null;}
        ListNode last = headB;
        while (last.next != null) {	last = last.next;}
        last.next = headB;

        ListNode fast = headA;
        ListNode slow = headA;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                fast = headA;
                while (slow != fast) {
                    slow = slow.next;
                    fast = fast.next;
                }
                last.next = null;
                return fast;
            }
        }
        last.next = null;
        return null;
    }
```




