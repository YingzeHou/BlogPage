# RearrangeLastN

Given a singly linked list of integers `l` and a non-negative integer `n`, move the last `n` list nodes to the beginning of the linked list.

Example

* For `l = [1, 2, 3, 4, 5]` and `n = 3`, the output should be\
  `solution(l, n) = [3, 4, 5, 1, 2]`;
* For `l = [1, 2, 3, 4, 5, 6, 7]` and `n = 1`, the output should be\
  `solution(l, n) = [7, 1, 2, 3, 4, 5, 6]`.

## Idea

{% hint style="info" %}
Corner case+Iteration+divide-->merge
{% endhint %}

Check if n is 0 or greater than length of list, if so, cannot rearrange

Get length of list and iterate first half from 0 to (length-n), store in head

Get second half from length-n to end, store as newHead

newHead.next = head

## Code

```java
ListNode<Integer> solution(ListNode<Integer> l, int n) {
    int count = 0;
    ListNode<Integer> curr = l;
    while(curr!=null){
        count++;
        curr = curr.next;
    }
    if(count<=n || n==0){
        return l;
    }
    ListNode<Integer> head = l;
    int currInd = 0;
    ListNode<Integer> next = null;
    while(l!=null && currInd<(count-n)){
        next = l.next;
        currInd++;
        if(currInd>=(count-n)){
            l.next = null;
        }
        else{
            l = next;
        }
    }
    ListNode<Integer> newHead = next;
    while(next!=null && next.next!=null){
        next = next.next;
    }
    
    next.next = head;
    return newHead;
    
}
```
