# 707. Design Linked List

Date: 15/07/2024
Design your implementation of the linked list. You can choose to use a singly or doubly linked list.
A node in a singly linked list should have two attributes: val and next. val is the value of the current node, and next is a pointer/reference to the next node.  
If you want to use the doubly linked list, you will need one more attribute prev to indicate the previous node in the linked list. Assume all nodes in the linked list are 0-indexed.

Implement the MyLinkedList class:

MyLinkedList() Initializes the MyLinkedList object.  
int get(int index) Get the value of the indexth node in the linked list. If the index is invalid, return -1.  
void addAtHead(int val) Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.  
void addAtTail(int val) Append a node of value val as the last element of the linked list.  
void addAtIndex(int index, int val) Add a node of value val before the indexth node in the linked list. If index equals the length of the linked list, the node will be appended to the end of the linked list. If index is greater than the length, the node will not be inserted.  
void deleteAtIndex(int index) Delete the indexth node in the linked list, if the index is valid.

> Example 1:

> Input
> ["MyLinkedList", "addAtHead", "addAtTail", "addAtIndex", "get", "deleteAtIndex", "get"]
> [ [ ], [1], [3], [1, 2], [1], [1], [1] ]
> Output
> [null, null, null, null, 2, null, 3]

> Explanation
> MyLinkedList myLinkedList = new MyLinkedList();
> myLinkedList.addAtHead(1);
> myLinkedList.addAtTail(3);
> myLinkedList.addAtIndex(1, 2); // linked list becomes 1->2->3
> myLinkedList.get(1); // return 2
> myLinkedList.deleteAtIndex(1); // now the linked list is 1->3
> myLinkedList.get(1); // return 3

# Solution

```java
    class MyLinkedList {
    // Inner class for list node
    class ListNode {
        int val;
        ListNode next;
        ListNode() {}
        ListNode(int val) {
            this.val = val;
        }
    }

    int size;
    // Virtual head
    ListNode head;

    // Initialize linked list
    public MyLinkedList() {
        size = 0;
        head = new ListNode(0); // Sentinel node
    }

    // Get the value of the index-th node in the linked list. If the index is invalid, return -1.
    public int get(int index) {
        if (index < 0 || index >= size) {
            return -1;
        }
        ListNode cur = head;
        // We have a virtual head, so we iterate index + 1 times
        for (int i = 0; i <= index; i++) {
            cur = cur.next;
        }
        return cur.val;
    }

    // Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
    public void addAtHead(int val) {
        ListNode newNode = new ListNode(val);
        newNode.next = head.next;
        head.next = newNode;
        size++;
    }

    // Append a node of value val as the last element of the linked list.
    public void addAtTail(int val) {
        ListNode newNode = new ListNode(val);
        ListNode cur = head;
        while (cur.next != null) {
            cur = cur.next;
        }
        cur.next = newNode;
        size++;
    }

    // Add a node of value val before the index-th node in the linked list. If index equals the length of the linked list, the node will be appended to the end of the linked list.
    // If index is greater than the length, the node will not be inserted.
    public void addAtIndex(int index, int val) {
        if (index > size) {
            return;
        }
        if (index < 0) {
            index = 0;
        }
        size++;
        ListNode pred = head;
        for (int i = 0; i < index; i++) {
            pred = pred.next;
        }
        ListNode toAdd = new ListNode(val);
        toAdd.next = pred.next;
        pred.next = toAdd;
    }

    // Delete the index-th node in the linked list, if the index is valid.
    public void deleteAtIndex(int index) {
        if (index < 0 || index >= size) {
            return;
        }
        size--;
        ListNode pred = head;
        for (int i = 0; i < index; i++) {
            pred = pred.next;
        }
        pred.next = pred.next.next;
    }
}

/**
 * Your MyLinkedList object will be instantiated and called as such:
 * MyLinkedList obj = new MyLinkedList();
 * int param_1 = obj.get(index);
 * obj.addAtHead(val);
 * obj.addAtTail(val);
 * obj.addAtIndex(index, val);
 * obj.deleteAtIndex(index);
 */

```

---

## Extension

### ArrayList

- quick in query
- slow in add/delete
- big CPU usage

### LinkedList

#### Node - 2 parts

1. Value in Node
2. The next value's position

```java
Linkedlist linkedList = new LinkedList(0);
linkedList.add(11);
linkedList.add(12)
```

step 0: int size = 0; Node first = (11's position)
step 1: - value (11) - Node next (null)
step 2: - value (11) - Node next (12's position) - value2 (12) - Node next (null)
