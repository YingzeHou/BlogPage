---
description: 'ID: 45'
---

# Jump Game II

Given an array of non-negative integers `nums`, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

You can assume that you can always reach the last index.

```
Input: nums = [2,3,1,1,4]
Output: 2
Explanation: The minimum number of jumps to reach the last index is 2. 
Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

## Idea

{% hint style="info" %}
Greedy + condition check
{% endhint %}

Similar to Jump Game I, but this time, keep track of a global max and a local max, which only when current index reach its local max, step should be increment

Iteratively check for the global max that can be achieved from a index, when index == local max, step+=1, update local max to global max. Otherwise, only increment current index

## Code

```java
public int jump(int[] nums) {
    if(nums.length==1){
        return 0;
    }
    if(nums[0]>=nums.length-1){
        return 1;
    }
    int step = 0;
    int i = 1;
    int currMax = nums[0];
    int max = nums[0];
    while(i<=currMax && i<nums.length){
        max = Math.max(max, i+nums[i]);
        if(i==currMax || i==nums.length-1){
            step++;
            currMax = max;
        }
        i++;
    }
    return step;
}
```
