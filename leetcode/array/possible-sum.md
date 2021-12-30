# Possible Sum

You have a collection of coins, and you know the values of the `coins` and the `quantity` of each type of coin in it. You want to know how many distinct sums you can make from non-empty groupings of these coins.

Example

For `coins = [10, 50, 100]` and `quantity = [1, 2, 1]`, the output should be\
`solution(coins, quantity) = 9`.

Here are all the possible sums:

* `50 = 50`;
* `10 + 50 = 60`;
* `50 + 100 = 150`;
* `10 + 50 + 100 = 160`;
* `50 + 50 = 100`;
* `10 + 50 + 50 = 110`;
* `50 + 50 + 100 = 200`;
* `10 + 50 + 50 + 100 = 210`;
* `10 = 10`;
* `100 = 100`;
* `10 + 100 = 110`.

As you can see, there are `9` distinct sums that can be created from non-empty groupings of your coins.

## Idea

{% hint style="info" %}
HashSet, traversal
{% endhint %}

Iterate through each coin and corresponding quantity, add resulting sum to HashSet

Make a duplicate of current sums for every coin index, so that each coin can be added to the sums without affecting the original set.

The set will automatically remove sum duplicates

## Code

```java
int solution(int[] coins, int[] quantity) {
    HashSet<Integer> sums = new HashSet<>();
    sums.add(0);
    for(int i = 0; i<coins.length; i++){
        List<Integer> currSum = new ArrayList<>(sums);
        for(Integer curr: currSum){
            for(int j = 1; j<=quantity[i]; j++){
                sums.add(curr+coins[i]*j);
            }
        }
    }
    return sums.size()-1;
}
```
