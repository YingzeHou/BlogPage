---
description: 'ID: 130'
---

# Surrounding Regions

Given an `m x n` matrix `board` containing `'X'` and `'O'`, _capture all regions that are 4-directionally surrounded by_ `'X'`.

A region is **captured** by flipping all `'O'`s into `'X'`s in that surrounded region.

![](https://assets.leetcode.com/uploads/2021/02/19/xogrid.jpg)

```
Input: board = [["X","X","X","X"],["X","O","O","X"],["X","X","O","X"],["X","O","X","X"]]
Output: [["X","X","X","X"],["X","X","X","X"],["X","X","X","X"],["X","O","X","X"]]
Explanation: Surrounded regions should not be on the border, 
which means that any 'O' on the border of the board are not flipped 
to 'X'. Any 'O' that is not on the border and it is not connected to 
an 'O' on the border will be flipped to 'X'. 
Two cells are connected if they are adjacent cells connected 
horizontally or vertically.
```

## Idea

{% hint style="info" %}
BFS / DFS
{% endhint %}

DFS requires less coding, so DFS

Check the borders of the matrix and see index with value 'O'. Do DFS from this specific value to see all connected components to this border and update them to an arbitrary value, like '#'

Iterate all elements in matrix and update all other 'O' to 'X' since these are not connected to border, and update all '#' to 'O' since they are border 'O's that cannnot be flipped

## Code

```javascript
public void solve(char[][] board) {
    int m= board.length;
    int n = board[0].length;    
    for(int i=0;i<m;i++){
        for(int j=0;j<n;j++){ 
            if((i==0||i==m-1||j==0||j==n-1) && board[i][j]=='O')
                dfs(board,i,j,m-1,n-1);
        }
    }    
    for(int i=0;i<m;i++){
       for(int j=0;j<n;j++){
           if(board[i][j]=='O')
               board[i][j]='X';
            else if(board[i][j]=='#')
                board[i][j]='O';
        }
    } 
}
    
public void dfs(char[][] board,int i,int j,int ROW,int COL){        
    if(i<0||i>ROW||j<0||j>COL||board[i][j]=='#'||board[i][j]=='X')
        return;    
    board[i][j]='#';    
    dfs(board,i+1,j,ROW,COL);
    dfs(board,i-1,j,ROW,COL);
    dfs(board,i,j+1,ROW,COL);
    dfs(board,i,j-1,ROW,COL);
    
    return; 
}
```
