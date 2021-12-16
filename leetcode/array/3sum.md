---
description: 'ID: 15'
---

# 3Sum

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

## Idea

{% hint style="info" %}
For loop + two pointer
{% endhint %}

Sort the given list for speed up

Iterate from the beginning of nums\[] from 0-->length-1, set left = i & right = length-1

check sum of i, left, right-->left++ if smaller than 0; right++ if bigger than 0; add to result if ==0

```java
public List<List<Integer>> threeSum(int[] nums) {
        List<Integer> numsList = new ArrayList<>();
        for(int i: nums){
            numsList.add(i);
        }
        Collections.sort(numsList);
        List<List<Integer>> result = new ArrayList<>();

        for(int i = 0; i<numsList.size(); i++){
            int left = i+1;
            int right = numsList.size()-1;
            while(left<right){
                if(numsList.get(i)+numsList.get(left)+numsList.get(right)<0){
                    left++;
                    continue;
                }
                else if(numsList.get(i)+numsList.get(left)+numsList.get(right)>0){
                    right--;
                    continue;
                }
                else if(numsList.get(i)+numsList.get(left)+numsList.get(right)==0){
                    List<Integer> curr = new ArrayList<>();
                    curr.add(numsList.get(i));
                    curr.add(numsList.get(left));
                    curr.add(numsList.get(right));
                    
                    if(!result.contains(curr)){
                         result.add(curr);
                    }
                    left++;
                }
                
            }
        }
        
        
        
        return result;
    }
```

