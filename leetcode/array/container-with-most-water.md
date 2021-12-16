---
description: 'ID: 11'
---

# Container with most water

Given `n` non-negative integers `a1, a2, ..., an` , where each represents a point at coordinate `(i, ai)`. `n` vertical lines are drawn such that the two endpoints of the line `i` is at `(i, ai)` and `(i, 0)`. Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.

## Idea

{% hint style="info" %}
Two pointers
{% endhint %}

left=0, right=length-1;&#x20;

getArea for each left--right pair, left++ if height\[left]\<height\[right], otherwise right++

## Code

```java
public int maxArea(int[] height) {
        int left = 0;
        int right = height.length-1;
        
        int max = 0;
        while(left<right){
            if(getArea(height, left, right)>max){
                max = getArea(height, left, right);    
            }
            if(height[left]<height[right]){
                left++;
            }
            else{
                right--;
            }
        }
        
        return max;
    }
    
    private int getArea(int[] height, int left, int right){
        int h = height[left]<height[right]?height[left]:height[right];
        int w = right-left;
        return h*w;
    }
```
