---
description: 'ID: 1463'
---

# Cherry Pickup

You are given a `rows x cols` matrix `grid` representing a field of cherries where `grid[i][j]` represents the number of cherries that you can collect from the `(i, j)` cell.

You have two robots that can collect cherries for you:

* **Robot #1** is located at the **top-left corner** `(0, 0)`, and
* **Robot #2** is located at the **top-right corner** `(0, cols - 1)`.

Return _the maximum number of cherries collection using both robots by following the rules below_:

* From a cell `(i, j)`, robots can move to cell `(i + 1, j - 1)`, `(i + 1, j)`, or `(i + 1, j + 1)`.
* When any robot passes through a cell, It picks up all cherries, and the cell becomes an empty cell.
* When both robots stay in the same cell, only one takes the cherries.
* Both robots cannot move outside of the grid at any moment.
* Both robots should reach the bottom row in `grid`.

![](https://assets.leetcode.com/uploads/2020/04/29/sample\_1\_1802.png)

```
Input: grid = [[3,1,1],[2,5,1],[1,5,5],[2,1,1]]
Output: 24
Explanation: Path of robot #1 and #2 are described in color green and blue respectively.
Cherries taken by Robot #1, (3 + 2 + 5 + 2) = 12.
Cherries taken by Robot #2, (1 + 5 + 5 + 1) = 12.
Total of cherries: 12 + 12 = 24.
```

## Idea

{% hint style="info" %}
Dynammic Programming + Bottom Up + Two object DP
{% endhint %}

Since the movement of robot1 and robot2 can interact with each other, meaning that we cannot calculate robot1 first and then calculate robot2, so that we need to move robot 1 and 2 at the same time.

Therefore, they will always be on the same row but different columns. So we can build a dp array of \[grid.length]\[grid\[0].length]\[grid\[0].length].

Each index of dp array has the meaning of the largest value that can be obtained from robot1 at \[row]\[c1] and robot2 at \[row]\[c2]. For example, dp\[3]\[0]\[3] means the largest cherry pick that can be obtained from robot1 at 3,0 in grid, and robot2 at 3,3 in grid

Therefore, we can apply bottom up approach so that the last row of the grid is just the value itself. If robot 1 and 2 are not having the same column number, they can get two cherry pick values in the grid. But if they are having the same column number, they can only get a single cherry pick value.

For topper layers from the last row, each index of dp can be calculated from the max of all 9 combinations of 3 direction and 2 robots movements.

Finally, we can pop the dp\[0]\[0]\[grid\[0].length-1] to get the max cherry pick count when starting from the top left and top right corner of the grid

## Code

```java
public int cherryPickup(int[][] grid) {
    int[][][] dp = new int[grid.length][grid[0].length][grid[0].length];
    for(int r = grid.length-1; r>=0; r--){
        for(int c1 = 0; c1<grid[0].length; c1++){
            for(int c2 = 0; c2<grid[0].length; c2++){
                int result = 0;
                result+=grid[r][c1];
                    
                if(c1!=c2){
                    result+=grid[r][c2];
                }
                    
                if(r!=grid.length-1){
                    int max = getMax(grid[0].length, r, c1, c2, dp);
                    result+=max;
                }
                dp[r][c1][c2] = result; 
            }
        }
    }
        
    return dp[0][0][grid[0].length-1];
}
    
int getMax(int n, int row, int col1, int col2, int[][][] dp){
    int max = 0;
    for (int newCol1 = col1 - 1; newCol1 <= col1 + 1; newCol1++) {
        for (int newCol2 = col2 - 1; newCol2 <= col2 + 1; newCol2++) {
            if (newCol1 >= 0 && newCol1 < n && newCol2 >= 0 && newCol2 < n) {
                    max = Math.max(max, dp[row + 1][newCol1][newCol2]);
            }
        }
    }
    return max;
}
```
