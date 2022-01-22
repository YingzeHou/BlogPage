---
description: ID:141
---

# Linked List Cycle

Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true` _if there is a cycle in the linked list_. Otherwise, return `false`.

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

```
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
```

## Idea

{% hint style="info" %}
Slow+fast pointer
{% endhint %}

Since we don't know when the tail of the linked list happens, we cannot just iterate and find null since we don't know where it's suppose to terminate

General thought of assigning a slow moving pointer and a fast moving pointer, when fast moving one meets the slow moving one, meaning that the fast one have cycled over and meet the slow one, otherwise, there's no cycle

## Code

```java
public boolean hasCycle(ListNode head) {
    if (head == null) {
        return false;
    }
        
    ListNode slow = head;
    ListNode fast = head;
        
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;        
        if (slow == fast) {
            return true;
        }
    }
    
    return false;
}
```
