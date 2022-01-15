---
description: ID:300
---

# Longest Increasing Subsequence

Given an integer array `nums`, return the length of the longest strictly increasing subsequence.

A **subsequence** is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, `[3,6,2,7]` is a subsequence of the array `[0,3,1,6,2,2,7]`.\


```
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
```

## Idea

{% hint style="info" %}
Dynammic Programming + Condition check
{% endhint %}

Construct a DP array to store the max length of subsequence when reaching index i. Therefore, for index i, check for previous elements and if previous element is smaller than the value at index i in nums, means that current element can form a subsequence with the previous one

In this case, get the max of DP\[i] and DP\[prev]. Since we are checking all the element previous to index i, we can always get the max length we can get for index i by the max from previous indexes.

After we got the max for i, we can increment DP\[i] by 1 for the resulting subsequence length when reaching index i

## Code

```java
public int lengthOfLIS(int[] nums) {
    int[] dp = new int[nums.length];
    for(int i = 0; i<nums.length; i++){
        dp[i] = 0;
        for(int j = i-1; j>=0; j--){
            if(nums[j]<nums[i]){
                dp[i] = Math.max(dp[i], dp[j]);
            }
        }
        dp[i] = dp[i]+1;
    }
        
    int max = 0;
    for(int i: dp){
        max = max>i?max:i;
    }
    return max;
}
```
