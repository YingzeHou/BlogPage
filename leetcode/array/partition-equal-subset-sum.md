---
description: 'ID: 416'
---

# Partition Equal Subset Sum

Given a **non-empty** array `nums` containing **only positive integers**, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.

```
Input: nums = [1,5,11,5]
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].
```

## Idea

{% hint style="info" %}
Dynamic Programming + Bottom up
{% endhint %}

Since there are n elements in nums, if the sum of elements if odd, cannot be partitioned

Else, need to find if there's possible combinations using a part of these n elements to form a sum of overall sum/2 {(1+5+11+5)/2 = 11 in this case}

Construct a dp matrix with all four elements and all possible sum from 1\~11. Check if a possible sum can be achieved based on some or all of elements. For example, sum=1 can be achieved because element 1 is in the array; sum=11 can be achieved since 11 is in the array

If a sum is not exactly equals to the element value, we need to check if combinations of elements can achieve this sum. For example, sum=6 can be achieved since 1+5=6

Therefore, the equation is like:&#x20;

`if(nums[i]==j) dp[i][j] = true // Exactly same as expected sum`

`if(nums[i]>j) dp[i][j] = dp[i-1][j] // Current value larger than target sum, check if previous elements are able to form the target sum`

`if(nums[i]<j) dp[i][j] = dp[i-1][j] || dp[i-1][j-nums[i]] // Current value small, check if previous combinations works or if previous sum + current value can form the target sum`

Finally, check if dp\[nums.length-1]\[sum-1] is true or not, meaning if it's possible to use part of all elements to form the overall sum/2&#x20;

## Code

```java
public boolean canPartition(int[] nums) {
        int sum = 0;
        for(int i: nums){
            sum+=i;
        }
        if(sum%2!=0){
            return false;
        }
        
        sum = sum/2;
        
        boolean[][] dp = new boolean[nums.length][sum];
        for(int i=0; i<dp.length; i++){
            for(int j=0; j<dp[0].length; j++){
                if(i==0){
                    if(nums[i]==j+1){
                        dp[i][j] = true;
                    }
                }
                else{
                    if(nums[i]>(j+1)){
                        dp[i][j] = dp[i-1][j];
                    }
                    else if(nums[i]==j+1){
                        dp[i][j] = true;
                    }
                    else{
                        dp[i][j] = dp[i-1][j] || dp[i-1][j-nums[i]];
                    }
                }
            }
        }
        return dp[nums.length-1][sum-1];
    }
```
