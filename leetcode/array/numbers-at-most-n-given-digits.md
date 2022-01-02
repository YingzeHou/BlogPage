---
description: ID:902
---

# Numbers At Most N Given Digits

Given an array of `digits` which is sorted in **non-decreasing** order. You can write numbers using each `digits[i]` as many times as we want. For example, if `digits = ['1','3','5']`, we may write numbers such as `'13'`, `'551'`, and `'1351315'`.

Return _the number of positive integers that can be generated_ that are less than or equal to a given integer `n`.

```
Input: digits = ["1","3","5","7"], n = 100
Output: 20
Explanation: 
The 20 numbers that can be written are:
1, 3, 5, 7, 11, 13, 15, 17, 31, 33, 35, 37, 51, 53, 55, 57, 71, 73, 75, 77.
```

## Idea

{% hint style="info" %}
Dynamic Programming + Math
{% endhint %}

If n has k digits, any combination with length \<k is valid: n=100, all 1 and 2 digit numbers are valid

So, check how many combinations can be formed from digits: 1,3,5,7,11,13,15,17..... --> length^1+length^2. Therefore, # combinations = length^1 + ... + length^k-1

For number with same # digits, iterate from least sig bit, if the bit is greater than the corresponding bit of n, then any combinations from bit k+1 to the end is valid. For example, if n=350, least sig=0, not valid, second bit = 5, 1,3 is smaller, so no matter what least sig is, if second bit is 1 or 3, it's valid....

If the bit is equals to corresponding bit of n, then number of valid combinations from k+1 bit is valid. For example, n=350, second bit = 5, from digits, 5 is equals to 5, so only when least sig bit is smaller or equals to 0, the resulting number is valid, in this case, the # of valid is 0, as no digit is smaller or equals to 0 from digits

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
