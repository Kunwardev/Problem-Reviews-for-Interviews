---
platform: GeeksForGeeks
difficulty: Medium
tags:
  - bits
date_solved: 2026-11-03
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/game-of-xor1541/1)
* **Difficulty:** Medium
* **Time Complexity:** $O(n)$
* **Space Complexity:** $O(1)$

## Approach

- **If n is even:** The result is **`0`** (every element appears an even number of times across all subarrays, so they cancel out).

- **If n is odd:** The result is the **XOR sum of all elements at even indices** (indices )(0, 2, 4, .... n-1)), because elements at even indices appear an odd number of times, while elements at odd indices appear an even number of times.

## Solution
```java
public int subarrayXor(int[] arr) {
        // code here
        int length = arr.length;
        int result = 0;
        if(length % 2 == 1){
            for(int i=0;i<length; i+=2){
                result ^= arr[i];
            }
        }
        return result;
    }