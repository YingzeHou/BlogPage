---
description: ID:221
---

# Maximal Square

Given an `m x n` binary `matrix` filled with `0`'s and `1`'s, _find the largest square containing only_ `1`'s _and return its area_.



![](https://assets.leetcode.com/uploads/2020/11/26/max1grid.jpg)

```
Input: matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
Output: 4
```

## Idea

{% hint style="info" %}
Dynamic Programming
{% endhint %}

If a cell is surrounded by 1s, this cell can form a new square with 1 more length (\[i-1]\[j], \[i]\[j-1]\[i-1]\[j-1] all 1, \[i]\[j] can form a 2x2 square)

Extensively, if (\[i-1]\[j], \[i]\[j-1]\[i-1]\[j-1] all already in a 2x2 square, \[i]\[j] can form a 3x3 square)

So, heuristic: dp\[i]\[j] = Min(dp\[i-1]\[j], dp\[i]\[j-1], dp\[i-1]\[j-1]) + 1

## Code

```java
public int maximalSquare(char[][] matrix) {
        int rows = matrix.length, cols = matrix[0].length;
        int[][] dp = new int[rows + 1][cols + 1];
        int maxsqlen = 0;
        for (int i = 1; i <= rows; i++) {
            for (int j = 1; j <= cols; j++) {
                if (matrix[i-1][j-1] == '1'){
                    dp[i][j] = Math.min(Math.min(dp[i][j - 1], dp[i - 1][j]), dp[i - 1][j - 1]) + 1;
                    maxsqlen = Math.max(maxsqlen, dp[i][j]);
                }
            }
        }
        return maxsqlen * maxsqlen;
    }
```
