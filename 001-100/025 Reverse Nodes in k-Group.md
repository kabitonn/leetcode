# [Reverse Nodes in k-Group](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)

## 1. 题目描述\(困难\)

## 2. 思路

## 3. 解决方法

### 3.1 递归

```java
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode cur = head;
        int n = 1;
        while(cur!=null&&n++<k) {
            cur = cur.next;
        }
        if(cur==null)
            return head;
        cur = head;
        ListNode[] listNodes = new ListNode[k];
        for(int i=0;i<k;i++) {
            listNodes[i] = cur;
            cur = cur.next;
        }
        head.next = reverseKGroup(listNodes[k-1].next, k);
        for(int i=k-1;i>0;i--) {
            listNodes[i].next = listNodes[i-1];
        }
        return listNodes[k-1];
    }
```

```java
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode cur = head;
        int n = 1;
        while(cur!=null&&n++<k) {
            cur = cur.next;
        }
        if(cur==null)
            return head;
        ListNode tmp = cur.next;
        cur.next = null;
        ListNode newHead = reverse(head);
        head.next = reverseKGroup(tmp, k);
        return newHead;
    }
    public ListNode reverse(ListNode head) {
        ListNode cur = head;
        ListNode newHead = null;
        ListNode next;
        while(cur!=null) {
            next = cur.next;
            cur.next = newHead;
            newHead = cur;
            cur = next;
        }
        return newHead;
    }
```

### 3.2 迭代

```java
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode start = new ListNode(0);
        start.next = head;
        ListNode cur = start.next;
        ListNode connect = start;
        ListNode[] listNodes = new ListNode[k];
        while(true) {
            //当轮头结点
            ListNode tmp = cur;
            int n = 1;
            while(cur!=null&&n++<k) {
                cur = cur.next;
            }
            if(cur==null)
                break;
            cur = tmp;
            for(int i=0;i<k;i++) {
                listNodes[i] = cur;
                cur = cur.next;
            }

            for(int i=k-1;i>0;i--) {
                listNodes[i].next = listNodes[i-1];
            }
            //接续点
            connect.next = listNodes[k-1];
            connect = listNodes[0];
            connect.next = cur;
        }
        return start.next;
    }
```

```java
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode start = new ListNode(0);
        start.next = head;
        ListNode cur = start.next;
        ListNode connect = start;
        while(true) {
            //当轮头结点
            ListNode tmp = cur;
            int n = 1;
            while(cur!=null&&n++<k) {
                cur = cur.next;
            }
            if(cur==null)
                break;
            //下一轮首结点next cur
            ListNode next = cur.next;
            cur.next = null;
            //当轮反转
            ListNode newHead = reverse(tmp);
            //接续点
            connect.next = newHead;
            connect = tmp;
            connect.next = next;
            cur = next;
        }
        return start.next;
    }
    public ListNode reverse(ListNode head) {
    	ListNode cur = head;
    	ListNode newHead = null;
    	ListNode next;
    	while(cur!=null) {
    		next = cur.next;
    		cur.next = newHead;
    		newHead = cur;
    		cur = next;
    	}
    	return newHead;
    }
```





