---
description: 'ID: 31'
---

# Next Permutation

Implement **next permutation**, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such an arrangement is not possible, it must rearrange it as the lowest possible order (i.e., sorted in ascending order).

```
Input: nums = [1,2,3,6,5,4]
Output: [1,2,4,3,5,6]
```

## Idea

{% hint style="info" %}
Swap + reverse + condition checkx
{% endhint %}

Check if given nums\[] in desending order, if yes, just reverse

Locate ith element that breaks the desending order, check from the end for the first element greater than ith element

Swap these two element and reverse the i+1th element to end(1,2,3,6,5,4-->1,2,4,6,5,3\[6 is not the least element greater than 4, but 3 is]-->1,2,4,3,5,6)

## Code

```java
public void nextPermutation(int[] nums) {
        int i = nums.length - 2;
        while (i >= 0 && nums[i + 1] <= nums[i]) {
            i--;
        }
        if (i >= 0) {
            int j = nums.length - 1;
            while (nums[j] <= nums[i]) {
                j--;
            }
            swap(nums, i, j);
        }
        reverse(nums, i + 1);
    }

    private void reverse(int[] nums, int start) {
        int i = start, j = nums.length - 1;
        while (i < j) {
            swap(nums, i, j);
            i++;
            j--;
        }
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
```
