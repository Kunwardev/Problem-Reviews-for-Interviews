---
platform: GeeksforGeeks
difficulty: Medium
tags:
  - maths
date_solved: 2026-10-13
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/squares-in-reactangle3340/1)
* **Difficulty:** Medium
* **Time Complexity:** $O(log(min(n, m)))$
* **Space Complexity:** $O(1)$

## Approach
Whichever is the smaller number, it will be the first square that will be created. now, count how many squares will get created and then the remainder is the length left.

## Solution
```java
public int minSquares(int n, int m) {
        // code here
        int count = 0;
        while(n > 0 && m > 0){
            if(m > n){
                count += m / n;
                m = m % n;
            }
            else{
                count += n / m;
                n = n % m;
            }
        }
        return count;
    }