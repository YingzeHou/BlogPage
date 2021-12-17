---
description: 'ID: 48'
---

# Rotate Image

You are given an `n x n` 2D `matrix` representing an image, rotate the image by **90** degrees (clockwise).

You have to rotate the image [**in-place**](https://en.wikipedia.org/wiki/In-place\_algorithm), which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.

![](https://assets.leetcode.com/uploads/2020/08/28/mat1.jpg)

```
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]
```

## Idea

{% hint style="info" %}
Pure matrix manipulation, index trick
{% endhint %}

For a odd size matrix (3x3), only first two row and first one column should be considered, other indexes can be calculated based on these info.

For a even size matrix(4x4), first two row and first two column should be considered.

So, i in range(0, (n+1)/2), j in range(0. n/2)

## Code

```java
public void rotate(int[][] matrix) {
        int n = matrix.length;
        for(int i = 0; i<(n+1)/2; i++){
            for(int j = 0; j<n/2; j++){
                int temp = matrix[n - 1 - j][i];
                matrix[n - 1 - j][i] = matrix[n - 1 - i][n - j - 1];
                matrix[n - 1 - i][n - j - 1] = matrix[j][n - 1 -i];
                matrix[j][n - 1 - i] = matrix[i][j];
                matrix[i][j] = temp;
            }
        }
    }
```
