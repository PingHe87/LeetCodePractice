# 24. Swap Nodes in Pairs

Date: 18/07/2024
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

> Input: head = [1,2,3,4]
> Output: [2,1,4,3]

> Input: head = []
> Output: []

> Input: head = [1]
> Output: [1]

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
    public ListNode swapPairs(ListNode head) {
        //base case
        if(head == null || head.next == null){
            return head;
        }
        ListNode newN = head.next;
        ListNode newNode = swapPairs(newN.next);
        newN.next = head;
        head.next = newNode;

        return newN;
    }
}
```
