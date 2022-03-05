---
description: 'ID: 740'
---

# Delete and Earn

You are given an integer array `nums`. You want to maximize the number of points you get by performing the following operation any number of times:

* Pick any `nums[i]` and delete it to earn `nums[i]` points. Afterwards, you must delete **every** element equal to `nums[i] - 1` and **every** element equal to `nums[i] + 1`.

Return _the **maximum number of points** you can earn by applying the above operation some number of times_.

```
Input: nums = [2,2,3,3,3,4]
Output: 9
Explanation: You can perform the following operations:
- Delete a 3 to earn 3 points. All 2's and 4's are also deleted. nums = [3,3].
- Delete a 3 again to earn 3 points. nums = [3].
- Delete a 3 once more to earn 3 points. nums = [].
You earn a total of 9 points.
```

## Idea

{% hint style="info" %}
Dynamic programming + cluster + store all possible values
{% endhint %}

Since all same number can be added together without being deleted, same numbers should be clustered and calculate the sum of same numbers

Get the max number among the list and create an array of length max+1 to store all possible sums of a given number, e.g: arr\[2] means the sum of all 3 (start from index 0, so plus 1)

Use the dp array to traverse the sum storage array. If current number is previous number+2, meaning that previous sum can add to current sum: dp\[i-2]+arr\[i]; If current number is previous number+1, meaning that current sum is deleted when calculating the previous sum, so that can only be dp\[i-1]. Get the max among these two possible combinations

dp\[dp.length-1] is the result of the max value obtaine

## Code

```java
public int deleteAndEarn(int[] nums) {
    if(nums.length==1){
        return nums[0];
    }
    if(nums.length==2 && Math.abs(nums[1]-nums[0])==1){
        return Math.max(nums[1], nums[0]);
    }
    Hashtable<Integer, Integer> table = new Hashtable<>();
    int max = 0;
    for(int i: nums){
        if(i>max){
            max = i;
        }
        if(table.get(i)==null){
            table.put(i, 1);
        }
        else{
            table.put(i, table.get(i)+1);
        }
    }
        
    int[] arr = new int[max+1];
    for(int key: table.keySet()){
        arr[key] = key*table.get(key);
    }
    
    int[] dp = new int[arr.length];
    dp[0] = arr[0];
    dp[1] = Math.max(arr[0],arr[1]);
    for(int i = 2; i<dp.length; i++){
        dp[i] = Math.max(dp[i-2]+arr[i], dp[i-1]);
    }
    return dp[dp.length-1];
}
```

