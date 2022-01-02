---
description: 'ID: 82'
---

# Remove Duplicates From Sorted List

Given the `head` of a sorted linked list, _delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list_. Return _the linked list **sorted** as well_.\


![](https://assets.leetcode.com/uploads/2021/01/04/linkedlist1.jpg)

```
Input: head = [1,2,3,3,4,4,5]
Output: [1,2,5]
```

## Idea

{% hint style="info" %}
DummyHead + prev track
{% endhint %}

Make a dummyHead in order to treat duplicates in the middle and duplicates at the head the same. For example, 1,2,3,3,4,4,5 has duplicates in the middle, while 1,1,1,2,3 has duplicates at head. With dummyHead, 1,1,1,2,3 can be treated as duplicates in the middle as well.

Use given head for traversal purpose, and use a reference (prev) to dummyHead for update purpose. If there's duplicates, use while loop to reach the end of this duplicates group, can update the next of prev to the next of head. If no duplicates, advance prev by one step, which is the same as the original head.

## Code

```java
public ListNode deleteDuplicates(ListNode head) {
        if(head==null){
            return head;
        } 
        ListNode dummyHead = new ListNode(101, head);
        ListNode prev = dummyHead;
        while(head!=null){
            int base = head.val;
            if(head.next!=null && head.next.val==base){
                while(head.next!=null && head.next.val==base){
                    head = head.next;
                }
                prev.next = head.next;
            }
            else{
               prev = prev.next; 
            }
            head = head.next;
        }
        return dummyHead.next;
    }
```
