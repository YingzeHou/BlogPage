---
description: ID:394
---

# Decode String

Given an encoded string, return its decoded string.

The encoding rule is: `k[encoded_string]`, where the `encoded_string` inside the square brackets is being repeated exactly `k` times. Note that `k` is guaranteed to be a positive integer.

You may assume that the input string is always valid; No extra white spaces, square brackets are well-formed, etc.

Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, `k`. For example, there won't be input like `3a` or `2[4]`.

```
Input: s = "3[a2[c]]"
Output: "accaccacc"
```

## Idea

{% hint style="info" %}
Stack + StringBuilder
{% endhint %}

Keep two stack to track most inner layer number and corresponding string

When 0\~9 met, update number to store the new number

When \[ is met, push current number to numStack and push new StringBuilder to stringStack

When ] is met, pop number from numStack, which is the most inner bracket layer number, and pop StringBuilder from stringStack for the corresponding string inside this bracket

If after poping stringStack, stack if not empty, meaning that this is not the most outer layer, update the previous StringBuilder by peek() with current number of current string (after poping c and 2, string stack not empty, so update a to be a+2c=acc)

Else if stack is empty, meaning is the outmost layer, update result string

If lowercase letter is met, peek() to get current string and update by appending current letter

## Code

```java
public String decodeString(String s) {
        Stack<StringBuilder> stringStack = new Stack<>();
        Stack<Integer> numStack = new Stack<>();
        StringBuilder result = new StringBuilder();
        
        int num = 0;
        for(int i =0; i<s.length(); i++){
            if(s.charAt(i)>='0' && s.charAt(i)<='9'){
                num = num*10+s.charAt(i)-'0';
            }
            else if(s.charAt(i)=='['){
                numStack.push(num);
                stringStack.push(new StringBuilder());
                num=0;
            }
            else if(s.charAt(i)==']'){
                int n = numStack.pop();
                StringBuilder str = stringStack.pop();
                StringBuilder strR = stringStack.size()==0?result: stringStack.peek();
                for(int j = 0; j<n; j++){
                    strR.append(str);
                }
            }
            else{
                StringBuilder str = stringStack.size()==0?result: stringStack.peek();
                str.append(s.charAt(i));
            }
        }
        return result.toString();
        
    }
```
