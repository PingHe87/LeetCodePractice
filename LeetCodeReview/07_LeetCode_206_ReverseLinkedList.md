# 206. Reverse Linked List

Date: 18/07/2024
Given the head of a singly linked list, reverse the list, and return the reversed list.

> Input: head = [1,2,3,4,5]
> Output: [5,4,3,2,1]
> Input: head = [ ]
> Output: [ ]

## Reasoning

```java
// head = [1, 2, 3]
1 -> 2 -> 3 -> null
// 1 would be the last one;
prev -> 1 -> 2 -> 3 -> null
 ^      ^
null   cur
```

## Solution

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode cur = head;
        ListNode temp = null;
        while(cur != null){
            temp = cur.next;
            cur.next = prev;
            prev = cur;
            cur = temp;
        }
        return prev;
    }
}
```
