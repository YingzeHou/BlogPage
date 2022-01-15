# Restore Binary Tree

Let's define _inorder_ and _preorder_ traversals of a binary tree as follows:

* _Inorder_ traversal first visits the left subtree, then the root, then its right subtree;
* _Preorder_ traversal first visits the root, then its left subtree, then its right subtree.

For example, if tree looks like this:

```
    1
   / \
  2   3
 /   / \
4   5   6
```

then the traversals will be as follows:

* _Inorder_ traversal: `[4, 2, 1, 5, 3, 6]`
* _Preorder_ traversal: `[1, 2, 4, 3, 5, 6]`

Given the _inorder_ and _preorder_ traversals of a binary tree `t`, but not `t` itself, restore `t` and return it.

## Idea

{% hint style="info" %}
Recursion + Array truncate
{% endhint %}

Since Preorder can give us the sequence from root to left to right & Inorder gives the sequence from left to root to right, so that current root is always the first element in Preorder, and the left subtree is always the part of array to the left of root element in Inorder array.

For example, Current root=1 in preorder, so from Inorder we can see, 4,2 is the left part of 1 and 5,3,6 is the right part of 1

Therefore, when we found a root, we construct based on the left and right sub tree. The base case is then when the left to a root is empty or the right to a root is empty, the root iteself is a leave for some ancester root

## Code

```javascript
Tree<Integer> solution(int[] inorder, int[] preorder) {
    if(inorder.length==0){
        return null;
    }
    if(inorder.length==1){
        return new Tree<Integer>(inorder[0]);
    }
    Tree<Integer> currRoot = new Tree(preorder[0]);
    int currRootInd = 0;
    for(int i = 0; i<inorder.length; i++){
        if(inorder[i]==currRoot.value){
            currRootInd = i;
            break;
        }
    }
    currRoot.left = solution(Arrays.copyOfRange(inorder, 0, currRootInd), Arrays.copyOfRange(preorder, 1, preorder.length));
    currRoot.right = solution(Arrays.copyOfRange(inorder, currRootInd+1, inorder.length), Arrays.copyOfRange(preorder, currRootInd+1, preorder.length));
    return currRoot;
    
}
```

