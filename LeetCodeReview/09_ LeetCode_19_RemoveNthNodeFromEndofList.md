# 19. Remove Nth Node From End of List

Date: 24/07/2024
Given the head of a linked list, remove the nth node from the end of the list and return its head.

> Example 1:
> Input: head = [1,2,3,4,5], n = 2
> Output: [1,2,3,5]

> Example 2:
> Input: head = [1], n = 1
> Output: [ ]

## Solution

-2 POINTERS

```java
//we want to delete the 2nd Node from end, it's 4
//set a fast pointer, a slow pointer
//faster one is (2+1) faster than the slower one.
1 -> 2 -> 3 -> 4 -> 5 -> null
^              ^
|              |
slow          fast
//when the faster one point to null, the slow one point to the Node we need to manipulate, and the next one is the Node we want to delete.
1 -> 2 -> 3 -> 4 -> 5 -> null
          ^              ^
          |              |
         slow          fast
```

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode fast = head, slow = head;
        for( int i = 0; i < n; i++) fast = fast.next;
        if(fast == null) return head.next;
        while(fast.next != null){
            fast = fast.next;
            slow = slow.next;
        }
        slow.next = slow.next.next;
        return head;
    }
}
```
