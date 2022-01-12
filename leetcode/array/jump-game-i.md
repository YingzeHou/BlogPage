---
description: 'ID: 55'
---

# Jump Game I

You are given an integer array `nums`. You are initially positioned at the array's **first index**, and each element in the array represents your maximum jump length at that position.

Return `true` _if you can reach the last index, or_ `false` _otherwise_.

```
Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

## Idea

{% hint style="info" %}
Greedy + traversal
{% endhint %}

Start from the beginning, calculate the max index that can be reached from that index. If final index >= nums.length-1, means that can step out, which means can reach end

For calculating, update max to Math.max(i+nums\[i], max)

## Code

```java
public boolean canJump(int[] nums) {
    int max = nums[0];
    for(int i = 1; i<=max && i<nums.length; i++){
        max = Math.max(max, nums[i]+i);
    }
    return max>=nums.length-1;
}
```
