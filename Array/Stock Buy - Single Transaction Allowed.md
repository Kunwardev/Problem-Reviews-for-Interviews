---
platform: GeeksForGeeks
difficulty: Medium
tags:
  - array
  - greedy
  - sliding-window
date_solved: 2026-09-29
---


* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/buy-stock-2/1)
* **Difficulty:** Medium
* **Time Complexity:** $O(n)$
* **Space Complexity:** $O(1)$

## Approach
Try to find the minimum price in the loop and also find the max difference in each step 

## Solution
```java
public int maximumProfit(int prices[]) {
        // Code here
        int minYet = prices[0];
        int res = 0;
        for(int i=1;i<prices.length;i++){
            minYet = Math.min(prices[i], minYet);
            res = Math.max(res, (prices[i]-minYet));
        }
        return res;
    }