# Swap Lex Order

Given a string `str` and array of `pairs` that indicates which indices in the string can be swapped, return the [lexicographically largest](keyword://lexicographical-order-for-strings) string that results from doing the allowed swaps. You can swap indices any number of times.

Example

For `str = "abdc"` and `pairs = [[1, 4], [3, 4]]`, the output should be\
`solution(str, pairs) = "dbca"`.

By swapping the given indices, you get the strings: `"cbda"`, `"cbad"`, `"dbac"`, `"dbca"`. The lexicographically largest string in this list is `"dbca"`.

## Idea

{% hint style="info" %}
Tree structure + connected component + string manipulation
{% endhint %}

Construct tree for pairs and find connect component to know which indexes can be freely swapped (Ex: 1,4,3 are connected, so any sequence: 143, 134, 341, 314 .... is valid). Each connected component is free to swap and not interfere with each other (Ex: 1,4 and 7,8,9 means 1,4 can freely swap and 7,8,9 can freely swap, but nothing in 1,4 can appear in 7,8,9)

Find the largest lex order of the corresponding connected component (Ex: for 1,4,3-->a,d,c so the largest lex order is dca, which correspond to 431)

Replace the corresponding order to the original string (Ex: original: abdc-->1234, new sequence is 431-->dbca, b is index 2, cannot change)

{% hint style="danger" %}
TreeSet is different from HashSet that TreeSet remain a natural order: set{1,4,3} appears to be {1,3,4} for TreeSet while remain unordered for HashSet
{% endhint %}

## Code

```java
String solution(String str, int[][] pairs) {
    Map<Integer, Set<Integer>> map = new HashMap<>();
    for(int[] pair: pairs){
        int u = pair[0];
        int v = pair[1];
        
        map.putIfAbsent(u, new HashSet<>());
        map.putIfAbsent(v, new HashSet<>());
        
        map.get(u).add(v);
        map.get(v).add(u);
    }
    
    List<TreeSet<Integer>> sccs = new ArrayList<>();
    Set<Integer> visited = new HashSet<>();
    
    for(Integer curr: map.keySet()){
        if(!visited.contains(curr)){
            TreeSet<Integer> scc = new TreeSet();
            scc.add(curr);
            dfs(visited, scc, map, curr);
            sccs.add(scc);
        }
    }
    
    char[] arr = str.toCharArray();
    for(TreeSet<Integer> scc: sccs){
        List<Character> ordered = new ArrayList<>();
        for(int ind: scc){
            ordered.add(arr[ind-1]);
        }
        Collections.sort(ordered);
        Collections.reverse(ordered);
        
        int i = 0;
        for(int ind: scc){
            arr[ind-1] = ordered.get(i);
            i++;
        }
    }
    return String.valueOf(arr);
}

void dfs(Set<Integer> visited, TreeSet<Integer> scc, Map<Integer, Set<Integer>> map, int curr){
    for(int currNeigh: map.get(curr)){
        if(!visited.contains(currNeigh)){
            visited.add(currNeigh);
            scc.add(currNeigh);
            dfs(visited, scc, map, currNeigh);
        }
    }
}
```
