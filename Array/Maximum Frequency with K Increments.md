---
platform: GeeksforGeeks
difficulty: Medium
tags:
  - array
  - sliding-window
date_solved: 2026-10-07
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/maximum-frequency-1662528911/1)
* **Difficulty:** Medium
* **Time Complexity:** $O(nlogn)$
* **Space Complexity:** $O(1)$

## Approach
Sort the Array. 
Now use Sliding Window, to count the number of increments needed to convert all the numbers in sliding window to the rightmost number in the Array. 
Then compare with Max Frequency and replace if it is bigger. 
## Solution
```java
public int maxFrequency(int[] arr, int k) {
        // code here
        Arrays.sort(arr);
        int left = 0;
        long sum = 0;
        int maxFreq = 1;
        for(int right = 0; right < arr.length; right++){
            sum += arr[right];
            while(arr[right] * (right - left + 1) - sum > k){
                sum -= arr[left++];
            }
            maxFreq = Math.max(maxFreq, right - left + 1);
        }
        return maxFreq;
    }