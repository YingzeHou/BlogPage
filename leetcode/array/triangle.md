---
description: ID:120
---

# Triangle

Given a `triangle` array, return _the minimum path sum from top to bottom_.

For each step, you may move to an adjacent number of the row below. More formally, if you are on index `i` on the current row, you may move to either index `i` or index `i + 1` on the next row.

```
Input: triangle = [[2],[3,4],[6,5,7],[4,1,8,3]]
Output: 11
Explanation: The triangle looks like:
   2
  3 4
 6 5 7
4 1 8 3
The minimum path sum from top to bottom is 2 + 3 + 5 + 1 = 11 (underlined above).
```

## Idea

{% hint style="info" %}
Dynamic Programming + think from the lowest level of triangle
{% endhint %}

Construct dp\[] on bottom level elements

Iterate up with i in range(length-2{4-2=2: third level in this case}, 0}, and j in range(0, i{number of element in ith level = i})

Select the min from dp\[j], dp\[j+1] to plus their common parent and update dp\[j] {once go up a level, a element from the end of dp is disregarded: when calculating third level 6,5,7 from 4,1,8,3, dp update to (1+6,1+5,3+7, 3), the last element remain unchanged}

## Code

```java
public int minimumTotal(List<List<Integer>> triangle) {
        int[] dp = new int[triangle.size()];
        for(int i = 0; i<triangle.size(); i++){
            dp[i] = triangle.get(triangle.size()-1).get(i);
        }
        
        for(int i = triangle.size()-2; i>=0; i--){
            for(int j = 0; j<=i; j++){
                dp[j] = Math.min(dp[j],dp[j+1])+triangle.get(i).get(j);
            }
        }
        
        return dp[0];
    }
```
