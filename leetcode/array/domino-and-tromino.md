---
description: 'ID: 790'
---

# Domino and Tromino

You have two types of tiles: a `2 x 1` domino shape and a tromino shape. You may rotate these shapes.

![](https://assets.leetcode.com/uploads/2021/07/15/lc-domino.jpg)

Given an integer n, return _the number of ways to tile an_ `2 x n` _board_. Since the answer may be very large, return it **modulo** `109 + 7`.

In a tiling, every square must be covered by a tile. Two tilings are different if and only if there are two 4-directionally adjacent cells on the board such that exactly one of the tilings has both squares occupied by a tile.

![](https://assets.leetcode.com/uploads/2021/07/15/lc-domino1.jpg)

```
Input: n = 3
Output: 5
Explanation: The five different ways are show above.
```

## Idea

{% hint style="info" %}
Dynamic Programming + Pattern finding
{% endhint %}

![](../../.gitbook/assets/IMG\_6BF4677D1CCC-1.jpeg)

## Code

```java
public int numTilings(int n) {
        if(n==1){
            return 1;
        }
        if(n==2){
            return 2;
        }
        int mod = (int)(Math.pow(10,9)+7);
        
        int[] dp = new int[n+1];
        dp[0] = 1;
        dp[1] = 1;
        dp[2] = 2;
        
        for(int i=3;i<=n;i++){
            dp[i] = ((2*dp[i-1])%mod)+dp[i-3];
            dp[i] %= mod;
        }
        
        return dp[n];
    }
```
