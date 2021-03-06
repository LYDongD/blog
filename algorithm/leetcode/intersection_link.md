## Intersection Of Two Links

### 问题

```
Write a program to find the node at which the intersection of two singly linked lists begins.
For example, the following two linked lists:
A:          a1 → a2
               ↘
c1 → c2 → c3
               ↗
B:     b1 → b2 → b3
begin to intersect at node c1.
Notes:
If the two linked lists have no intersection at all, return null.
The linked lists must retain their original structure after the function returns.
You may assume there are no cycles anywhere in the entire linked structure.
Your code should preferably run in O(n) time and use only O(1) memory.

```

### 思路1

* 分别计算2个链表的长度
* 长的先走一定步数直到两条链表在同一起跑线
* 两条链表同时走，如果节点相同，则为交汇处


```

public static ListNode getIntersectionNode(ListNode headA, ListNode headB) {

        //count the A length
        ListNode cursor = headA;
        int linkListALength = 0;
        while (cursor != null) {
            cursor = cursor.next;
            linkListALength++;
        }

        cursor = headB;
        //count the B length
        int linkListBLength = 0;
        while (cursor != null) {
            cursor = cursor.next;
            linkListBLength++;
        }

        //move delta link node to keep in synchronize step
        ListNode cursorA = headA;
        ListNode cursorB = headB;
        int delta = linkListALength - linkListBLength;
        if (delta > 0) {
            for (int i = 0; i < delta; i++) {
                cursorA = cursorA.next;
            }
        } else if (delta < 0) {
            for (int i = 0; i < -delta; i++) {
                cursorB = cursorB.next;
            }
        }

        //move at the same time until intersection
        while (cursorA != null) {

            if (cursorA == cursorB) {
                return cursorA;
            }

            cursorA = cursorA.next;
            cursorB = cursorB.next;
        }

        return null;
    }

```


### 思路2

* 一起走，走2遍
* 第一遍达终点如果还没汇合，则交换链表走第二遍
* 两个链表都交换后，一定位于同一起跑线
* 如果节点相同，则为交汇处


```

 public static ListNode getIntersectionNode2(ListNode headA, ListNode headB) {

        if (headA == null || headB == null){
            return null;
        }

        ListNode cursorA = headA;
        ListNode cursorB = headB;
        while (cursorA != cursorB){
            cursorA = cursorA.next == null ? headB : cursorA.next;
            cursorB = cursorB.next == null ? headA : cursorB.next;
        }

        return cursorA;
    }


```