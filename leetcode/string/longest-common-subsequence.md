---
description: 'ID: 1143'
---

# Longest Common Subsequence

Given two strings `text1` and `text2`, return _the length of their longest **common subsequence**._ If there is no **common subsequence**, return `0`.

A **subsequence** of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

* For example, `"ace"` is a subsequence of `"abcde"`.

A **common subsequence** of two strings is a subsequence that is common to both strings.

```
Input: text1 = "abcde", text2 = "ace" 
Output: 3  
Explanation: The longest common subsequence is "ace" and its length is 3.
```

## Idea

{% hint style="info" %}
Dynammic Programming +  Bottom up
{% endhint %}

Truncate from the end of each string text, if the end of both string matches, then calculate the result for this particular index with the next index of both strings.

For example, dp\[i]\[j] = dp\[i+1]\[j+1]+1, since current i, j matchs, so the resulting subsequence length is the later one increment by 1

If not, get the max from dp\[i+1]\[j] and dp\[i]\[j+1]

## Code

```java
public int longestCommonSubsequence(String text1, String text2) {
    int n1=text1.length(),n2=text2.length();
    int[][] dp=new int[n1+1][n2+1];
    for(int i=n1-1;i>=0;i--)
        for(int j=n2-1;j>=0;j--)
        {
            if(text1.charAt(i)==text2.charAt(j))
                dp[i][j]=dp[i+1][j+1]+1;
            else
                dp[i][j]=Math.max(dp[i+1][j],dp[i][j+1]);
        }
    return dp[0][0];
}
```

## &#x20;
