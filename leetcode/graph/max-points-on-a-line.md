---
description: ID:149
---

# Max Points on a Line

Given an array of `points` where `points[i] = [xi, yi]` represents a point on the **X-Y** plane, return _the maximum number of points that lie on the same straight line_.

\
![](https://assets.leetcode.com/uploads/2021/02/25/plane2.jpg)

```
Input: points = [[1,1],[3,2],[5,3],[4,1],[2,3],[1,4]]
Output: 4
```

## Idea

{% hint style="info" %}
Math + Hashtable
{% endhint %}

Since the deterministic factor to decide whether two points are on a line, the slope of two is important. Therefore, we need to record the number of points with the same slope

But a key point is, like in the above example, (1,1),(2,3) and (4,1),(5,3) has the same slope, but they cannot be counted together since they are not on the same line.

Therefore, we need to construct a seperate table for each base point. For example, for base point(1,1), only (2,3) can be counted since they are of slope 2, but (4,1) and (5,3) will not be counted.

There's a special case, where two points are on a vertical line. In this case, the slope of deltaY/deltaX is undefined, since deltaX = 0. Therefore, we count this special case with another if condition.

## Code

```java
public int maxPoints(int[][] points) {
    if (points.length <= 2) return points.length;
    int result = 0;
    for (int i = 0;i<points.length;i++){
        Map<Double, Integer> map = new HashMap<>();
        int count = 1;
        int same = 0;
        for (int j = 0;j<points.length;j++){
            if(j != i){
                int firstX = points[i][0];
                int firstY = points[i][1];
            
                int secondX = points[j][0];
                int secondY = points[j][1];
    
                // vertical line
                if (firstX == secondX) {
                    count++;                    
                    continue;
                }
                double k = (double)(secondY - firstY) / (double)(secondX - firstX);
                map.put(k, map.getOrDefault(k, 1)+1);
                result = Math.max(result, map.get(k));
            }
        }
        result = Math.max(result, count);
    }
    return result;
}
```
