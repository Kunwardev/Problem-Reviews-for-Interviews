---
platform: GeeksForGeeks
difficulty: Medium
tags:
  - array
  - greedy
  - sliding-window
date_solved: 2026-09-29
---


* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/stock-buy-and-sell2615/1)
* **Difficulty:** Medium
* **Time Complexity:** $O(n)$
* **Space Complexity:** $O(1)$

## Approach
Everytime, the stock price is higher than the previous price. Add the difference to the profit. 

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