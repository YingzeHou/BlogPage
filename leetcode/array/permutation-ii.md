---
description: ID:47
---

# Permutation II

Given a collection of numbers, `nums`, that might contain duplicates, return _all possible unique permutations **in any order**._

```
Input: nums = [1,1,2]
Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

## Idea

{% hint style="info" %}
Recursion + seen\[] tracking
{% endhint %}

Construct recursion method "permute" with params: int\[] nums, List<>curr, List\<List<>> result, boolean\[] seen

Iterate from 0 index to end of nums; If index already seen, continue; If index element equals to previous one and previous one is not seen, meaning permutation with previous element in the front is been created, then makes no difference to use current index element as the front one (1,1,2==1,1,2), so continue

Else, add current index element to curr, seen\[index] = true, and recursively call on curr

## Code

```java
public List<List<Integer>> permuteUnique(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> curr = new ArrayList<>();
        boolean[] seen = new boolean[nums.length];
        permute(result, curr, seen, nums);
        return result;
    }
    
    private void permute(List<List<Integer>> result, List<Integer> curr, boolean[] seen, int[] nums){
        if(curr.size()==nums.length){
            result.add(new ArrayList(curr));
            return;
        }
        
        for(int i = 0; i<nums.length; i++){
            if(seen[i]){
                continue;
            }
            if(i > 0 && nums[i] == nums[i-1] && !seen[i-1]) continue;
            else{
                seen[i] = true;
                curr.add(nums[i]);
                permute(result, curr, seen, nums);
                seen[i] = false;
                curr.remove(curr.size()-1);
            }
        }
    }
```
