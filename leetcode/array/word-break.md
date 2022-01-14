---
description: ID:139
---

# Word Break

Given a string `s` and a dictionary of strings `wordDict`, return `true` if `s` can be segmented into a space-separated sequence of one or more dictionary words.

**Note** that the same word in the dictionary may be reused multiple times in the segmentation.

```
Input: s = "leetcode", wordDict = ["leet","code"]
Output: true
Explanation: Return true because "leetcode" can be segmented as "leet code".
```

## Idea

{% hint style="info" %}
Recursion + Memorization
{% endhint %}

Always start from the beginning of the string, check if there's a fit in wordDict for the starting substring.

If so, check for the later part of the string to check the starting substring in wordDict......

If the resulting substring after truncating the part that is equals to the dict word has a length=0, meaning all characters in the string found its corresponding dict word, then return true, since the entire string can be partitioned based on wordDict

Also, use a List or HashMap to keep track of already seen pattern. In corner cases like s = "aaaaaaaaaaaaab" and wordDict = \["a","aa","aaa","aaaaa"], we can save a lot of time when a previous pattern is already seen by returning false

## Code

```java
HashMap<String, Boolean> map = new HashMap<>();
// List<String> seen = new ArrayList<>();
public boolean wordBreak(String s, List<String> wordDict) {
    if(s.length()==0){
        return true;
    }
    if(map.containsKey(s)){
        return false;
    }
    for(String dict: wordDict){
        if(dict.length()<=s.length() && s.substring(0, dict.length()).equals(dict)){
            if(wordBreak(s.substring(dict.length()), wordDict)){
                return true;
            }
        }
    }
        
    map.put(s, false);
    return false;
}
```

