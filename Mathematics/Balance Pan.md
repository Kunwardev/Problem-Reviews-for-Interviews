---
platform: GeeksforGeeks
difficulty: Easy
tags:
  - maths
date_solved: 2026-10-10
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/balancing-pan5038/1)
* **Difficulty:** Easy
* **Time Complexity:** $O(log b)$
* **Space Complexity:** $O(1)$

## Approach
At each power of (a), choose (0), (+1), or (-1) to make the remaining target divisible by (a); it’s possible if the remainder reaches zero after all available weights.
## Solution
```java
public boolean balancePan(int a, int b) {
        // code here
        while (b > 0){
            int r = b % a;
            if(r == 0 || r == 1)
                b = b / a;
            else if(r == a - 1)
                b = (b+1) / a;
            else
                return false;
        }
        return true;
    }