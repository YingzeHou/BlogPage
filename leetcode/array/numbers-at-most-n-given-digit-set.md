---
description: 'ID: 902'
---

# Numbers At Most N Given Digit Set

Given an array of `digits` which is sorted in **non-decreasing** order. You can write numbers using each `digits[i]` as many times as we want. For example, if `digits = ['1','3','5']`, we may write numbers such as `'13'`, `'551'`, and `'1351315'`.

Return _the number of positive integers that can be generated_ that are less than or equal to a given integer `n`.\


```
Input: digits = ["1","4","9"], n = 1000000000
Output: 29523
Explanation: 
We can write 3 one digit numbers, 9 two digit numbers, 27 three digit numbers,
81 four digit numbers, 243 five digit numbers, 729 six digit numbers,
2187 seven digit numbers, 6561 eight digit numbers, and 19683 nine digit numbers.
In total, this is 29523 integers that can be written using the digits array.
```

## Idea

{% hint style="info" %}
Math+ Dynamic Programming
{% endhint %}

If n is a K digit number, than all combinations of K-1 digit number from digits can be valid, therefore, assume digits has N elements, than possible combinations are N^1+N^2+...+N^(K-1)

For combination with K digits, start from the least significant bit of n, for example, if n=1234, digits = \[1,2,3], then 1,2,3 all smaller than 4, fit--> 1,2 smaller than 3, so for any combination on the 4th digit place, fit (11,12,13,21,22,23), N^1 for 1 and N^1 for 2; for 3, equals 3, so only combinations that fit in 4th place can fit here, therefore, dp\[i] += dp\[i+1]

Then, by our reasoning above, `dp[i] = (number of d in D with d < S[i]) * ((D.length) ** (K-i-1))`, plus `dp[i+1]` if `S[i]` is in `D`.

## Code

```java
public int atMostNGivenDigitSet(String[] digits, int n) {
        String s = String.valueOf(n);
        int K = s.length();
        int res = 0;
        int numD = digits.length;
        for(int i = 1; i<K; i++){
            res+=Math.pow(numD, i);
        }
        
        int[] dp = new int[K+1];
        dp[K] = 1;
        
        for(int i=K-1; i>=0; i--){
            int si = s.charAt(i)-'0';
            for(String d: digits){
                if(Integer.valueOf(d)<si){
                    dp[i]+=Math.pow(digits.length, K-1-i);
                }
                else if(Integer.valueOf(d)==si){
                    dp[i]+=dp[i+1];
                }
            }
        }
        
        
        return res+dp[0];
    }
```
