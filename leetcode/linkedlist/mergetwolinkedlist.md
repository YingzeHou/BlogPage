---
description: 'ID: 21'
---

# MergeTwoLinkedList

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists in a one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return _the head of the merged linked list_.

![](https://assets.leetcode.com/uploads/2020/10/03/merge\_ex1.jpg)

```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

## Idea

{% hint style="info" %}
While loop, value comparison; Dummy head
{% endhint %}

Start from the smaller head, while loop to check if any of the list turns null

Compare and insert

## Code

```java
public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode();
        ListNode result = dummy;
        while(list1 != null && list2 != null){
            if (list1.val < list2.val){
                dummy.next = new ListNode(list1.val);
                list1 = list1.next;
            }else{
                dummy.next = new ListNode(list2.val);
                list2 = list2.next;
            }
            dummy = dummy.next;
        }
        dummy.next =(list1!=null)?list1:list2;
        return result.next;
    }
```
