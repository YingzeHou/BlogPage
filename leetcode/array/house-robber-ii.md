---
description: ID:213
---

# House Robber II

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are **arranged in a circle.** That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given an integer array `nums` representing the amount of money of each house, return _the maximum amount of money you can rob tonight **without alerting the police**_.

```
Input: nums = [2,3,2]
Output: 3
Explanation: You cannot rob house 1 (money = 2) and 
then rob house 3 (money = 2), because they are adjacent houses.
```

## Idea

{% hint style="info" %}
Dynamic Programming + case consider
{% endhint %}

Since the result of the last house can either use index 0 house or not use index 0 house. We can consider two cases: 1. Start from 0 to num.length-2 index, which exclude the last index; 2. Start from 1 to last index, which exclude the first index

Keep track of two max values which are appliable to either odd index or even index. For example, dp\[0]  = nums\[0] and dp\[1] = nums\[1]. Starting from index 2, current max value = Math.max(dp\[0]+nums\[2], dp\[1]); Then dp\[0]=dp\[1] and dp\[1] = current max.

Therefore, no adjacent index will use the max of adjacent index

## Code

```java
public int rob(int[] nums) {
    if(nums.length == 0) return 0;
    if(nums.length == 1) return nums[0];
    if(nums.length == 2) return Math.max(nums[0],nums[1]);        
    return Math.max(robHouses(nums, 0, nums.length-1),robHouses(nums, 1, nums.length));
}
    
    public int robHouses(int[] nums,int s, int e){
    int[] d = {nums[s], Math.max(nums[s], nums[s+1])};
    int cur = d[1];
    for(int i=s+2; i < e; i++){
        cur=Math.max(d[0]+nums[i], d[1]);
        d[0]=d[1];
        d[1]=cur;
    }
    return cur;
}
```
