# Convert Sorted Array to Binary Search Tree

Given an integer array `nums` where the elements are sorted in **ascending order**, convert _it to a **height-balanced** binary search tree_.

A **height-balanced** binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/18/btree1.jpg)

```
Input: nums = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
Explanation: [0,-10,5,null,-3,null,9] is also accepted:
```

## Idea

{% hint style="info" %}
Binary divide + recursion
{% endhint %}

Since left subtree need to be smaller than root and right subtree need to be larger than root, use left half and right half with regard to the root (mid index) to fill the tree

For example, mid index value = 0, -10 & 3 need to be in left sub tree and 5 & 9 need to be in right sub tree. Therefore, fill left of root 0 by picking the mid index value from \[-10,-3] (-10) and fill right of root 0 with mid index value from \[5,9] (9)

Then fill right of root -10 with -3 and fill left of root 9 with 5

## Code

```java
public TreeNode sortedArrayToBST(int[] nums) {
    return fill(0, nums.length-1, nums);
}    
public TreeNode fill(int low, int high, int[] nums){
    if(low>high){
        return null;
    }
    int mid = (low+high)/2;
    TreeNode root = new TreeNode(nums[mid]);
    if(low==high){
        return root;
    }
    root.left = fill(low, mid-1, nums);
    root.right = fill(mid+1, high, nums);
    return root;
}
```
