---
description: 'ID: 91'
---

# Decode Ways

A message containing letters from `A-Z` can be **encoded** into numbers using the following mapping:

```
'A' -> "1"
'B' -> "2"
...
'Z' -> "26"
```

To **decode** an encoded message, all the digits must be grouped then mapped back into letters using the reverse of the mapping above (there may be multiple ways). For example, `"11106"` can be mapped into:

* `"AAJF"` with the grouping `(1 1 10 6)`
* `"KJF"` with the grouping `(11 10 6)`

Note that the grouping `(1 11 06)` is invalid because `"06"` cannot be mapped into `'F'` since `"6"` is different from `"06"`.

Given a string `s` containing only digits, return _the **number** of ways to **decode** it_.

The test cases are generated so that the answer fits in a **32-bit** integer.

```
Input: s = "226"
Output: 3
Explanation: "226" could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).
```

## Idea

{% hint style="info" %}
Dynamic Programming + case condition
{% endhint %}

DP array keep track of the number of possible ways to decode starting from index 0 to index i

If s.charAt(i) == '0', means that the only way it can be valid is to combine with the previous character. Therefore, if the prev character is also '0' or greater than '1' or '2', no valid way to decode at all, return 0; If prev character is '1' or '2', then there's a valid combination of 10 or 20, so the number of ways to decode is = the number ways to decode from index 0 to index i-2

Else If s.charAt(i) <= '6', it can be itself valid or combine with the prev character if the prev character = '1' or '2', therefore, dp\[i] = dp\[i-2]+dp\[i-1];

Else if s.charAt(i) > '6', it can be itself valid or combine with prev char if prev char = '1', since the max valid number is 26, therefore 27, 28, 29 not valid.

Finally, return the dp\[lastIndex] to get the number of ways to decode from index 0 to index last

## Code

```java
public int numDecodings(String s) {
    if(s.charAt(0)=='0'){
        return 0;
    }
    int[] dp = new int[s.length()+1];
    dp[0] = 1;
    dp[1] = 1;
    for(int i =1; i<s.length(); i++){
        char curr = s.charAt(i);
        if(curr=='0'){
            if(s.charAt(i-1)=='0'){
                return 0;
            }
            if(s.charAt(i-1)>'0' && s.charAt(i-1)<='2'){
                dp[i+1] = dp[i-1];
            }
            else{
                return 0;
            }
        }
        else if(curr<='6'){
            if(s.charAt(i-1)>'0' && s.charAt(i-1)<='2'){
                dp[i+1] = dp[i]+dp[i-1];
            }
            else{
                dp[i+1]= dp[i];
            }
        }
        else{
            if(s.charAt(i-1)>'0' && s.charAt(i-1)<='1'){
                dp[i+1] = dp[i]+dp[i-1];
            }
            else{
                dp[i+1] = dp[i];
            }
        }
    }
    
    return dp[dp.length-1];
}
```
