---
description: ID:39
---

# Combination Sum

Given an array of **distinct** integers `candidates` and a target integer `target`, return _a list of all **unique combinations** of_ `candidates` _where the chosen numbers sum to_ `target`_._ You may return the combinations in **any order**.

The **same** number may be chosen from `candidates` an **unlimited number of times**. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

It is **guaranteed** that the number of unique combinations that sum up to `target` is less than `150` combinations for the given input.

```
Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
```

## Idea

{% hint style="info" %}
Recursion, in-place update
{% endhint %}

Construct recursive method "comb" with params: int\[] candidates, int target, List\<List>> result, List<>curr, int currIndex

If target==0 and curr not empty, a combination found, add to result

Iterate from currIndex, add currIndex element to curr, recursively call comb on curr with updated target value, if curr result in correct combination, execute base case above, else, return

After all element from a given index iterated, remove the last element from curr and go on iteration

## &#x20;Code

```java
public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> output = new ArrayList<>();
        List<Integer> curr = new ArrayList<>();
        comb(candidates, target, output, curr, 0);
        return output;
}
    private void comb(int[] candidates, int target, List<List<Integer>> output, List<Integer> curr, int currInd){
        if(target==0 && !curr.isEmpty()){
            output.add(new ArrayList<>(curr));
        }
        else{
            for(int i = currInd; i<candidates.length; i++){
                if(target-candidates[i]>=0){
                    curr.add(candidates[i]);
                
                    comb(candidates, target-candidates[i], output, curr, i);
                    curr.remove(curr.size()-1);
                }
            }
        }
    }
```
