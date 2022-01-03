---
description: 'ID: 32'
---

# Longest Valid Parentheses

Given a string containing just the characters `'('` and `')'`, find the length of the longest valid (well-formed) parentheses substring.

```
Input: s = "(()"
Output: 2
Explanation: The longest valid parentheses substring is "()".
```

## Idea

{% hint style="info" %}
Dynamic Programming / Stack
{% endhint %}

If use stack, we need to consider all combinations or start and end index and check if the substring from start to end index is a valid parantheses, cost O(n^3), too slow.

By using DP, we find patterns: `if s[i]==')' and s[i-1]=='(', there's a valid paratheses, so dp[i] = dp[i-2]+2`, where dp record the longest length when ending at index i. In this case, "()" gives an addition of 2 in length.&#x20;

if `s[i]==')' and s[i-1]==')'`, we need to check the length of s\[i-1] has formed and check if the element before the start of dp\[i-1] previous elements is '('. For example, if str=""(()())", last two indexes form )), so we need to see what is the max length ending at the first ). Since there's a ()(), so the max length ending at the first ) is 4. Therefore, check if the element 4 positions in front of i is ( or not. In this case, index 5 = ), index 4 = ), dp\[4] = 4-->str\[i-dp\[4]-1]=str\[0] = (, valid.

Similar to previous conditions, if str="()(()())", in addition to check if the starting position is ( or not, we need to know the max length achieved by the element previous to the starting position. For example, previous we got max length achieved by the last ) = dp\[7] = dp\[6]+2, since dp\[2]=(, but in this case, the starting () is also valid, therefore, we need to add dp\[1] as well, where 1 is the position in front of the starting position of (()())

## Code

```java
public int longestValidParentheses(String s) {
    int maxans = 0;
    int dp[] = new int[s.length()];
    for (int i = 1; i < s.length(); i++) {
        if (s.charAt(i) == ')') {
            if (s.charAt(i - 1) == '(') {
                dp[i] = (i >= 2 ? dp[i - 2] : 0) + 2;
            } else if (i - dp[i - 1] > 0 && s.charAt(i - dp[i - 1] - 1) == '(') {
                dp[i] = dp[i - 1] + ((i - dp[i - 1]) >= 2 ? dp[i - dp[i - 1] - 2] : 0) + 2;
            }
            maxans = Math.max(maxans, dp[i]);
        }
    }
    return maxans;
}
```

\
