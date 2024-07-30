# 142. Linked List Cycle II

Date: 24/07/2024
Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

Do not modify the linked list.

> Input: head = [3,2,0,-4], pos = 1
> Output: tail connects to node index 1
> Explanation: There is a cycle in the linked list, where tail connects to the second node.

# Solution

- 2 POINTERS

```java
//fast pointer -- 2 Nodes
//slow pointer -- 1 Nodes
//x -- from head to cycle's begining
//y -- begining to fast and slow's meet point
//2 -- meet point to cycles's begining

<----x---->
1 -> 2 -> 3 -> 4 -> 5
          ^         |
          |         ˇ
          8 <- 7 <- 6
```

```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {// Cycle exsits
                ListNode index1 = fast;
                ListNode index2 = head;
                // Find the begining
                while (index1 != index2) {
                    index1 = index1.next;
                    index2 = index2.next;
                }
                return index1;
            }
        }
        return null;
    }
}
```
