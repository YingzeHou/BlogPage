---
description: 'ID: 117'
---

# Populating Next Right Pointers in Each Node II

Given a binary tree

```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```

Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to `NULL`.

Initially, all next pointers are set to `NULL`.

![](https://assets.leetcode.com/uploads/2019/02/15/117\_sample.png)

```
Input: root = [1,2,3,4,5,null,7]
Output: [1,#,2,3,#,4,5,7,#]
Explanation: Given the above binary tree (Figure A), 
your function should populate each next pointer to point to its 
next right node, just like in Figure B. The serialized output is in 
level order as connected by the next pointers,
with '#' signifying the end of each level.
```

## Idea

{% hint style="info" %}
BFS
{% endhint %}

BFS on each level of the tree, keep track of previous node and if the previous node is not the last one of the level, set the current node as the next element of the previous node

{% hint style="danger" %}
Not best time efficient, but enhance on BFS
{% endhint %}

## Code

```java
public Node connect(Node root) {
    if(root==null){
        return null;
    }        
    Queue<Node> q = new LinkedList<>();
    q.offer(root);
    while(!q.isEmpty()){
       int size = q.size();
        Node prev = q.poll();
        size--;
        while(size-- >0){
            Node curr = q.poll();
            prev.next = curr;
            if(prev.left!=null){
                q.offer(prev.left);
            }
            if(prev.right!=null){
                q.offer(prev.right);
            }
            prev = curr;        
    }
        if(prev.left!=null){
            q.offer(prev.left);
        }
        if(prev.right!=null){
            q.offer(prev.right);
        }
    }
    return root;
}
```
