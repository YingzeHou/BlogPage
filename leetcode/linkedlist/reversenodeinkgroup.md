---
description: 'ID: 25'
---

# ReverseNodeInKGroup

Given the `head` of a linked list, reverse the nodes of the list `k` at a time, and return _the modified list_.

`k` is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of `k` then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.

![](https://assets.leetcode.com/uploads/2020/10/03/reverse\_ex1.jpg)

```
Input: head = [1,2,3,4,5], k = 2
Output: [2,1,4,3,5]
```

## Idea

{% hint style="info" %}
Recursion, corner cases
{% endhint %}

Check if k is greater than number of node in list, if not, return original list

If greater than length of list, curr is now at the last element of the first group, so keep track of the first element in next group.

Apply resversekgroup for next group, reverse curr group, use curr group head to connect next group reversed head etc.

## Code

```java
public ListNode reverseKGroup(ListNode l, int k) {
        if(l==null || l.next==null){
            return l;
        }
        ListNode curr = l;
        int len = 1;
        while(curr.next!=null && len<k){
            curr = curr.next;
            len++;
        }
        if(len<k){
            return l;
        }

        ListNode tempNode = curr.next;
        curr.next = null;
        ListNode tempList = reverseKGroup(tempNode, k);
        ListNode prev = reverse(l);
        l.next = tempList;
        return prev;
    }

    ListNode reverse(ListNode l){
        if(l==null){
            return l;
        }
        ListNode next = null;
        ListNode prev = null;
        ListNode curr = l;

        while(curr!=null){
            next = curr.next;
            curr.next= prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
```
