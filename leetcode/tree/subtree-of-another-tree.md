---
description: ID:572
---

# Subtree of Another Tree

Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.

A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.

![](https://assets.leetcode.com/uploads/2021/04/28/subtree1-tree.jpg)

```
Input: root = [3,4,5,1,2], subRoot = [4,1,2]
Output: true
```

## Idea

{% hint style="info" %}
BFS / DFS
{% endhint %}

When a node that is the same as the root of subRoot is found, do BFS to check all corresponding elements to see if the subtree is valid

Else check both the left and right sub part of current root to see if any node that matches the root of subRoot exists in these sub parts, then do BFS check

## Code

```java
public boolean isSubtree(TreeNode root, TreeNode subRoot) {

    if(root==null) return false;
    if(subRoot==null) return true;
    return helper(root,subRoot) || isSubtree(root.left,subRoot) || isSubtree(root.right,subRoot);
}
boolean helper(TreeNode r,TreeNode s){
    if(r==null && s==null) return true;
    if(r==null || s==null) return false;
    return (r.val==s.val) && helper(r.left,s.left) && helper(r.right,s.right);
}   
```
