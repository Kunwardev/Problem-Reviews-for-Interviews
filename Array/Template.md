---
platform:
difficulty:
tags:
date_solved:
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link]()
* **Difficulty:** Medium
* **Time Complexity:** $O(n)$
* **Space Complexity:** $O(1)$

## Approach
Briefly describe your logic here (e.g., "Greedy approach: add up every positive difference between consecutive days").

## Solution
```java
public int maximumProfit(int prices[]) {
    int profit = 0;
    for(int i = 1; i < prices.length; i++) {
        if(prices[i-1] < prices[i]) {
            profit += (prices[i] - prices[i-1]);
        }
    }
    return profit;
}