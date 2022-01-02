---
description: 'ID: 1010'
---

# Pairs of Songs with Total Duration Divisible by 60

You are given a list of songs where the ith song has a duration of `time[i]` seconds.

Return _the number of pairs of songs for which their total duration in seconds is divisible by_ `60`. Formally, we want the number of indices `i`, `j` such that `i < j` with `(time[i] + time[j]) % 60 == 0`.

```
Input: time = [30,20,150,100,40]
Output: 3
Explanation: Three pairs have a total duration divisible by 60:
(time[0] = 30, time[2] = 150): total duration 180
(time[1] = 20, time[3] = 100): total duration 120
(time[1] = 20, time[4] = 40): total duration 60
```

## Idea

{% hint style="info" %}
Counting +  Array store
{% endhint %}

Only need to consider the modulo of each duration length: if mod=0 or 30, then any 2 combinations can result in a valid song. If mod=1\~29 & 31\~59, then any complements can be group together to form the valid song

Traverse the time array and store number of corresponding mod into the array of length 60 (lengthArr)

Traverse the first half of lengthArr to check the count of each length modulo. If mod==0 or 30, use Cn2 to get the number of possible combinations to form a pair from all songs, else record the count of length k, and the count of length 60-k to get the product of these two counts to get the possible combinations with these two lengths (lengthArr\[3]=2 & lengthArr\[57]=3, so there are total of 2x3 combinations to form a divisible by 60 song)

## Code

```java
public int numPairsDivisibleBy60(int[] time) {
        int[] lengthArr = new int[60];
        for(int t: time){
            int len = t%60;
            lengthArr[len]++;
        }
        
        int result = 0;
        for(int i = 0; i<=30; i++){
            if(i==0){
                int zeroCount = lengthArr[0];
                if(zeroCount>1){
                    result += (zeroCount*(zeroCount-1))/2;
                }
            }
            else{
                if(i==30){
                    int thirtyCount = lengthArr[30];
                    if(thirtyCount>1){
                        result += (thirtyCount*(thirtyCount-1))/2;
                    }
                }
                else{
                    int thisCount = lengthArr[i];
                    int compCount = lengthArr[60-i];
                    result+= thisCount*compCount;
                }
                
            }
        }
        return result;
    }
```
