# 203. Remove Linked List Elements

Date: 13/07/2024

## Description

Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

> Input: head = [1,2,6,3,4,5,6], val = 6
> Output: [1,2,3,4,5]

## Reasoning

1. For linked list, if we want to remove a item, we could create a new head for this linked list so that it would be easier to do.
2. Time: O(N)
   Space: O(1)
   A linked list can be defined as:

```java
    class ListNode {
        int val;
        ListNode next;
        ListNode(int x) {
            val = x;
            }
        ListNode() {
        }
    }
    // If we have a linked list and aim to remove 6:
    1 -> 2 -> 6 -> 3 -> 4 -> 5 -> 6
    // initialize dummy and cur
    dummy -> 0 -> 1 -> 2 -> 6 -> 3 -> 4 -> 5 -> 6
    ^
    cur//starts from dummy

    // move cur to next node
    dummy -> 0 -> 1 -> 2 -> 6 -> 3 -> 4 -> 5 -> 6
                  ^
                 cur//cur.next.val = 2 != 6
    // keep the dummy stand to export the result, use the cur to track the change
```

## Solution

```java
    class Solution{
        public ListNode removeElements(ListNode head, int val){
            //creat a new dummy head
            ListNode dummy = new ListNode();
            dummy.next = head;
            //creat a new listnode cur to track the result
            ListNode cur = dummy;
            //if cur.next.val = val, remove the pointer to next value
            while(cur.next != null){
                if(cur.next.val == val){
                    cur.next = cur.next.next;
                }
                else{
                     //if cur.next.val != val, move the pointer
                    cur = cur.next;
                }
            }
            //return the listnode without dummyhead
           return dummy.next;
        }
    }
```
