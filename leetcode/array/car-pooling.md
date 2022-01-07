---
description: 'ID: 1094'
---

# Car Pooling

There is a car with `capacity` empty seats. The vehicle only drives east (i.e., it cannot turn around and drive west).

You are given the integer `capacity` and an array `trips` where `trip[i] = [numPassengersi, fromi, toi]` indicates that the `ith` trip has `numPassengersi` passengers and the locations to pick them up and drop them off are `fromi` and `toi` respectively. The locations are given as the number of kilometers due east from the car's initial location.

Return `true` _if it is possible to pick up and drop off all passengers for all the given trips, or_ `false` _otherwise_.

```
Input: trips = [[2,1,5],[3,3,7]], capacity = 4
Output: false
```

## Idea

{% hint style="info" %}
PriorityQueue / Array storage
{% endhint %}

Approach 1: Construct PriorityQueue for \[startStop, endStop] and pop one by one to check if there's a stop that result in a load > capacity

Approach 2: Construct a simple array of length 1001, since there's maximum of 1000 stops. Check each trip can add corresponding passenger number to start stop and minus number to end stop

Iterate through all stops and sum all, if there's a point that the load > capacity, return false

## Code

```java
public boolean carPooling(int[][] trips, int capacity) {
    int[] stops = new int[1001];
    int load = 0;
    for(int i = 0; i<trips.length; i++){
        stops[trips[i][1]]+=trips[i][0];
        stops[trips[i][2]]-=trips[i][0];
    }
    
    for(int i = 0; i<stops.length; i++){
        load+=stops[i];
        if(load>capacity){
            return false;
        }
    }
    return true;
}
```
