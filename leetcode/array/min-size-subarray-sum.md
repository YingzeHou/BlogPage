---
description: ID:209
---

# Min Size Subarray Sum

Given an array of positive integers `nums` and a positive integer `target`, return the minimal length of a **contiguous subarray** `[numsl, numsl+1, ..., numsr-1, numsr]` of which the sum is greater than or equal to `target`. If there is no such subarray, return `0` instead.

```
Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.
```

## Idea

{% hint style="info" %}
Two pointer (Sliding window is a bit slow)
{% endhint %}

Keep track of left element and right element, and shrink the left element (move toward right)

While the sum from left to right is greater or equals to target, shrink the left.

If not, check if the resulting sum is greater or equals to target, if so, increment result;&#x20;

When not, meaning that current left to right range is to small in sum, since we have traversed all elements to the left of left, so we increment right by 1, and shrink left again as previously.

{% hint style="danger" %}
Window doesn't need to be shrinked always from the beginning of the array and follow increment by 1 pattern
{% endhint %}

## Code

```java
public int minSubArrayLen(int target, int[] nums) {
    int res = Integer.MAX_VALUE;
    int left = 0, right = 0;
    int sum = 0;
    while(right<nums.length)
    {
        sum += nums[right];
        while(sum-nums[left]>=target){ // shrink left
            sum-=nums[left];
            left++;
        }
        if(sum>=target)
        {
            res = Math.min(res, right - left+1);
        }
        right++;
    }
    
    return res == Integer.MAX_VALUE?0:res;
}
```
