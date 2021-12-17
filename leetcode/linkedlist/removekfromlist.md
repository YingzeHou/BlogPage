# RemoveKFromList

Given a singly linked list of integers `l` and an integer `k`, remove all elements from list `l` that have a value equal to `k`.

Example

* For `l = [3, 1, 2, 3, 4, 5]` and `k = 3`, the output should be\
  `solution(l, k) = [1, 2, 4, 5]`;
* For `l = [1, 2, 3, 4, 5, 6, 7]` and `k = 10`, the output should be\
  `solution(l, k) = [1, 2, 3, 4, 5, 6, 7]`.

## Idea

{% hint style="info" %}
Iteration + in-loop while loop
{% endhint %}

Iterate from the beginning and eliminate leading k

Iterate the mid-part and eliminate any single k or contiguous k

## Code

```java
ListNode<Integer> solution(ListNode<Integer> l, int k) {
    if(l==null){
        return l;
    }
    ListNode<Integer> head = null;
    while(l!=null){
        if(l.value!=k){
            head = l;
            break;
        }
        l = l.next;
    }
    
    ListNode<Integer> curr = head;
    while(curr!=null && curr.next!=null){
        if(curr.next.value==k){
            ListNode<Integer> kNode = curr.next;
            while(kNode!=null){
                if(kNode.value!=k){
                    break;
                }
                kNode = kNode.next;
            }
            curr.next = kNode;
        }
        curr = curr.next;
    }
    return head;
}

```
