---
platform: GeeksforGeeks
difficulty: Medium
tags: [string, greedy]
date_solved: 2026-09-29
---

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/dsa/largest-number-with-one-swap-allowed/)
* **Difficulty:** Medium
* Time Complexity: O(n)
* Auxiliary Space: O(1)

## Approach

## Solution
```java
public String largestSwap(String s) {
    char[] arr = s.toCharArray();
    int n = s.length();
    int[] last = new int[10];
    for(int i=0; i<n; i++){
        last[arr[i]-'0'] = i;
    }
    
    for(int i=0; i<n; i++){
        for(int d=9; d>arr[i]-'0'; d--){
            if(last[d] > i){
                char temp = arr[i];
                arr[i] = arr[last[d]];
                arr[last[d]] = temp;
                return new String(arr);
            }
        }
    }
    return s;
}
