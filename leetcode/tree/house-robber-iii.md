---
description: ID:337
---

# House Robber III

The thief has found himself a new place for his thievery again. There is only one entrance to this area, called `root`.

Besides the `root`, each house has one and only one parent house. After a tour, the smart thief realized that all houses in this place form a binary tree. It will automatically contact the police if **two directly-linked houses were broken into on the same night**.

Given the `root` of the binary tree, return _the maximum amount of money the thief can rob **without alerting the police**_.

![](https://assets.leetcode.com/uploads/2021/03/10/rob1-tree.jpg)

```
Input: root = [3,2,3,null,3,null,1]
Output: 7
Explanation: Maximum amount of money the thief can rob = 3 + 3 + 1 = 7.
```

## Idea

{% hint style="info" %}
HashMap to store max from each node + Dynamic Programming
{% endhint %}

Starting from root, if root is null, return 0; else, sum the result of root.left and root.right

Since adjacent node cannot be robbed`:`

`result of root.left = root.left.left+root.left.right /`&#x20;

`root.right = root.right.left+root.right.right`

Since the result from root is result of root.left+result of root.right, we need to add the value of root as well.&#x20;

Pick the max from (result from root, result from left child, result from right child)

{% hint style="danger" %}
Use HashMap to store the seen node result, so that do not need to calculate the result from a seen node to save time cost
{% endhint %}

## Code

```java
public int rob(TreeNode root) {
        return rob(root, new HashMap<>());
    }

    public int rob(TreeNode root, Map<TreeNode, Integer> map) {
        
        if (root == null) return 0;

        if (map.containsKey(root)) return map.get(root);

        int ans = 0;

        if (root.left != null) {
            ans += rob(root.left.left, map) + rob(root.left.right, map);
        }

        if (root.right != null) {
            ans += rob(root.right.left, map) + rob(root.right.right, map);
        }

        ans = Math.max(ans + root.val, rob(root.left, map) + rob(root.right, map));
        map.put(root, ans);

        return ans;
    }
```
