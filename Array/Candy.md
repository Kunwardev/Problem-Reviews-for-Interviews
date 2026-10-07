---
platform: GeeksforGeeks
difficulty: Hard
tags:
  - array
  - greedy
date_solved: 2026-09-29
---

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/candy/1)
* **Difficulty:** Hard
* Time Complexity: O(n)
* Space Complexity: O(n)

## Approach

We need to give each child at least one candy, and every child with a higher rating than a neighbor must get more candies than that neighbor.

A simple greedy solution works in two passes:

1. Traverse from left to right.
   - If the current rating is greater than the previous rating, then the current child must have more candies than the previous child.
   - So, assign `candies[i] = candies[i - 1] + 1`.

2. Traverse from right to left.
   - If the current rating is greater than the next rating, then the current child must have more candies than the next child.
   - Update `candies[i] = max(candies[i], candies[i + 1] + 1)`.

This ensures both left-to-right and right-to-left constraints are satisfied. Finally, sum all values in the candies array.



## Solution
```java
public static int minCandyDistribute(int[] arr) {
    int[] candies = new int[arr.length];
    Arrays.fill(candies, 1);
    for(int i=1; i<arr.length; i++){
        if(arr[i] > arr[i-1]){
            candies[i] = candies[i-1] + 1;
        }
    }
    for(int i=arr.length-2; i>=0; i--){
        if(arr[i] > arr[i+1]){
            candies[i] = Math.max(candies[i], candies[i+1]+1);
        }
    }
    return Arrays.stream(candies).sum();
}