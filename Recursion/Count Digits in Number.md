---
platform: GeeksforGeeks
difficulty: Easy
tags:
  - recursion
date_solved: 2026-10-12
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/count-total-digits-in-a-number/1)
* **Difficulty:** Easy
* **Time Complexity:** $O(logn)$
* **Space Complexity:** $O(1)$

## Approach
Using Recursion and returning a counter when the number divided by 10 is turned to 0. 
Edge case if n == 0

## Solution
```java
public int countDigits(int n) {
        // Code here
        if(n == 0)
            return 1;
        int count = 0;
        return countDigitsHelper(n, count);
    }
    
    private int countDigitsHelper(int n, int count){
        if(n == 0)
            return count;
        return countDigitsHelper(n/10, count+1);
    }