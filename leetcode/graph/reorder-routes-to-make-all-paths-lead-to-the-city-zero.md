---
description: ID:1466
---

# Reorder Routes to Make All Paths Lead to the City Zero

There are `n` cities numbered from `0` to `n - 1` and `n - 1` roads such that there is only one way to travel between two different cities (this network form a tree). Last year, The ministry of transport decided to orient the roads in one direction because they are too narrow.

Roads are represented by `connections` where `connections[i] = [ai, bi]` represents a road from city `ai` to city `bi`.

This year, there will be a big event in the capital (city `0`), and many people want to travel to this city.

Your task consists of reorienting some roads such that each city can visit the city `0`. Return the **minimum** number of edges changed.

It's **guaranteed** that each city can reach city `0` after reorder.

![](https://assets.leetcode.com/uploads/2020/05/13/sample\_1\_1819.png)

```
Input: n = 6, connections = [[0,1],[1,3],[2,3],[4,0],[4,5]]
Output: 3
Explanation: Change the direction of edges show in red such that each node can reach the node 0 (capital).
```

## Idea

{% hint style="info" %}
Queue + BFS + Direction Reverse
{% endhint %}

Treat the graph as undirected. Start a dfs/bfs from the root, if you come across an edge in the forward direction, you need to reverse the edge.

Start from 0, find all undirected neighbors from 0: 1, 4, and check if there's a link between 0->1 or 0->4 in directed graph. Here we see that 0->1 is in directed graph, so 0->1 need to be reversed because all edges should be coming toward 0, instead of away from 0

## Code

```java
 public int minReorder(int n, int[][] connections) {
    Map<Integer, List<Integer>> undirected = new HashMap<>();
    Map<Integer, List<Integer>> directed = new HashMap<>();
        
    for(int[] c: connections){
        int from = c[0];
        int to = c[1];
        List<Integer> nei = directed.getOrDefault(from, new ArrayList<>());
        nei.add(to);
        directed.put(from, nei);
        List<Integer> listFrom = undirected.getOrDefault(from, new ArrayList<>());
        listFrom.add(to);
        undirected.put(from, listFrom);
        List<Integer> listTo = undirected.getOrDefault(to, new ArrayList<>());
        listTo.add(from);
        undirected.put(to, listTo); 
    }
    Queue<Integer> q = new LinkedList<>();
    Set<Integer> seen = new HashSet<>();
    seen.add(0);
    q.offer(0);
        
    int rev = 0;
    while(!q.isEmpty()){
        int curr = q.poll();
        for(int nei: undirected.get(curr)){
            if(!seen.contains(nei)){
                if(directed.get(curr) !=null && directed.get(curr).contains(nei)){
                    rev++;
                }
                q.offer(nei);
                seen.add(nei);
            }
        }
    }
    return rev;
}
```
