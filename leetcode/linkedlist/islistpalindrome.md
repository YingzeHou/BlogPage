# IsListPalindrome

Given a singly linked list of integers, determine whether or not it's a [palindrome](keyword://palindrome).

Example

* For `l = [0, 1, 0]`, the output should be\
  `solution(l) = true`;
* For `l = [1, 2, 2, 3]`, the output should be\
  `solution(l) = false`.

## Idea

{% hint style="info" %}
Stack
{% endhint %}

Push the copy of head to stack (1,2,2,1)

Start from start of head, pop stack (the last element added to stack)

If poped element = head element, continue iteration; else, not palindrome

## Code

```java
boolean solution(ListNode<Integer> head) {
    ListNode<Integer> slow = head;
    boolean ispalin = true;
    Stack<Integer> stack = new Stack<Integer>();

    while (slow != null) {
        stack.push(slow.value);
        slow = slow.next;
    }

    while (head != null) {

        int i = stack.pop();
        if (head.value == i) {
            ispalin = true;
        }
        else {
            ispalin = false;
            break;
        }
        head = head.next;
    }
    return ispalin;
}
```

## &#x20;

## &#x20;&#x20;
