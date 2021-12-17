---
description: 'ID: 36'
---

# Valid Sudoku

Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:

1. Each row must contain the digits `1-9` without repetition.
2. Each column must contain the digits `1-9` without repetition.
3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)

```
Input: board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: true
```

## Idea

{% hint style="info" %}
Brute force iteration, construct for each row/column/matrix
{% endhint %}

char\[]\[] for each row/column/matrix, iterate through

Construct checkvalid function to check repetition

## Code

```java
public boolean isValidSudoku(char[][] board) {
        boolean valid = true;
        // check row
        for(int i = 0; i<board.length; i++){
            char[][] row = new char[1][board[0].length];
            row[0] = board[i];
        
            if(!checkValid(row)){
                System.out.println("Row wrong");
                return false;
            }
        }
        for(int i = 0; i<board[0].length; i++){
            char[][] col = new char[board.length][1];
            for(int j = 0; j<board.length; j++){
                col[j][0] = board[j][i];
            }
        
            if(!checkValid(col)){
                System.out.println("Column wrong");
                return false;
            }
        }
        for(int i =0; i<board.length; i+=3){
            for(int j = 0; j<board[0].length; j+=3){
                char[][] matrix = new char[3][3];
                for(int m = 0; m<3; m++){
                    for(int n = 0; n<3; n++){
                        matrix[m][n] = board[i+m][j+n];
                    }
                }
                if(!checkValid(matrix)){
                    System.out.println("Matrix wrong");
                    return false;
                }
            }
        }
        return true;
    }
    
    private boolean checkValid(char[][] subBoard){
        List<Character> seen = new ArrayList<>();
        for(int i = 0; i<subBoard.length; i++){
            for(int j=0; j<subBoard[0].length; j++){
                if(subBoard[i][j]!='.'&&seen.contains(Character.valueOf(subBoard[i][j]))){
                    return false;
                }
                else{
                    seen.add(Character.valueOf(subBoard[i][j]));
                }
            }
        }
        return true;
    }
```
