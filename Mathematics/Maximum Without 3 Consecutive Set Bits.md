---
platform: GeeksforGeeks
difficulty: Medium
tags:
  - bits
date_solved: 2026-10-14
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/dsa/maximizing-unset-bits-in-integer-with-constraints/)
* **Difficulty:** Medium
* **Time Complexity:** $O(1)$
* **Space Complexity:** $O(1)$

## Approach
Check for all the places and if the consecutive 3 are 1, make the last one as 0

## Solution
```java
public int maxValue(int n) {
        // code here
        int res = n;
        for(int i=30;i>=2; i--){
            if((res & 1 << i) !=0 && (res & 1 << i-1) !=0 && (res & 1 << i-2) !=0 )
            {
                res &= ~(1 << (i-2));
            }
        }
        return res;
    }