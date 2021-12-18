---
description: 'ID: 22'
---

# Generate Parentheses

Given `n` pairs of parentheses, write a function to _generate all combinations of well-formed parentheses_.

```
Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
```

## Idea

{% hint style="info" %}
Recursion
{% endhint %}

If n=1, only () is possible; If n=2, (+\[n=1]+) / (+)+\[n=1]; If n=3, (+\[n=2]+) / (+\[n=1]+)+\[n=1] / (+)+\[n=2]

So, for n=k, it can contain all combination of n=k-1 and add new corresponding ( and ) to it

## Code

```vala
public List<String> generateParenthesis(int n) {
        List<String> ans = new ArrayList();
        if (n == 0) {
            ans.add("");
        } else {
            for (int c = 0; c < n; ++c)
                for (String left: generateParenthesis(c))
                    for (String right: generateParenthesis(n-1-c))
                        ans.add("(" + left + ")" + right);
        }
        return ans;
    }
```
