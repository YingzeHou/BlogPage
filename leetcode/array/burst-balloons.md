---
description: 'ID: 312'
---

# Burst Balloons

You are given `n` balloons, indexed from `0` to `n - 1`. Each balloon is painted with a number on it represented by an array `nums`. You are asked to burst all the balloons.

If you burst the `ith` balloon, you will get `nums[i - 1] * nums[i] * nums[i + 1]` coins. If `i - 1` or `i + 1` goes out of bounds of the array, then treat it as if there is a balloon with a `1` painted on it.

Return _the maximum coins you can collect by bursting the balloons wisely_.

```
Input: nums = [3,1,5,8]
Output: 167
Explanation:
nums = [3,1,5,8] --> [3,5,8] --> [3,8] --> [8] --> []
coins =  3*1*5    +   3*5*8   +  1*3*8  + 1*8*1 = 167
```

## Idea

{% hint style="info" %}
Dynamic Programming +  Sliding window
{% endhint %}

As nums\[-1] and nums\[length] can be treated as 1, original array can be converted to \[1,3,1,5,8,1]

When we burst a balloon, the coin count is equals to current burst plus max of left burst and right burst. For example, if we burst from 3 to 5, the max coins when bursting 1 is 1x1x8 + coins when bursting 3 + coins when bursting 5, since 3 and 5 is already bursted

Initially, when considering only one burst, we have bursting 3 = 1x3x1, bursting 1 = 3x1x5, bursting 5 = 1x5x8.... And when considering burst two balloons, we have bursting 3,1 = max(burst 1 frist, burst 3 first)-->If burst 1 first, coin = _**burst 3 without 1:**_ 1x3x5 + _**burst 1:** _ 3x1x5

Therefore, we need a **sliding window,** indicating the number of balloons burst we consider at a iteration, and the **left index** indicating the start of consideration \[1\~nums.length (3,1,5,8)], and the **right index** indicating the end of window (left+window-1), and a **i index** indicating which balloon in the window to burst last (considering 3,1,5, where left ind = 1, right ind = 3, i index can be either 1,2,3)

Iteratively fill up the dp matrix, we finally need to know the coin count when considering a sliding window of length = nums.length from the left index = 1 to right index = nums.length

Equation: `dp[left][right] = Max(dp[left][right], arr[left-1]*arr[i]*arr[right+1]+dp[left][i-1]+dp[i+1][right])`

![](../../.gitbook/assets/IMG\_9650B9348645-1.jpeg)

## Code

```java
public int maxCoins(int[] nums) {
    int[] arr = new int[nums.length+2];
    arr[0] = arr[arr.length-1] = 1;
    
    // Convert original nums to [1,3,1,5,8,1]
    for(int i = 1; i<=nums.length; i++){
        arr[i] = nums[i-1];
    }    
    int[][] dp = new int[nums.length+2][nums.length+2];       
    for(int window = 1; window<=nums.length; window++){ // number of balloons to consider
        for(int left = 1; left<=nums.length-window+1; left++){
            int right = left+window-1;
            for(int i = left; i<=right; i++){ // which balloon in the window considered to burst lastly
                dp[left][right] = Math.max(dp[left][right], arr[left-1]*arr[i]*arr[right+1]+dp[left][i-1]+dp[i+1][right]);
            }
        }
    }
    
    return dp[1][nums.length];
}
```
