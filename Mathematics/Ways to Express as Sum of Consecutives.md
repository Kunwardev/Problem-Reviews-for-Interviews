---
platform: GeeksforGeeks
difficulty: Medium
tags:
  - maths
date_solved: 2026-10-10
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/count-of-sum-of-consecutives3741/1)
* **Difficulty:** Medium
* **Time Complexity:** $O(sqrt(n))$
* **Space Complexity:** $O(1)$

## Approach
Let the first number of valid sequence having k elements sum equal to n is a.

The sequence a, (a+1), (a+2), ..., (a+k-1).

- a + (a+1) + (a+2) + .... + (a+k-1) = n
- k * a + ( 1 + 2 + .... + k-1 ) = n
- a = (n - baseSum ) / k ; where baseSum = k * (k - 1) /2

For each k starting from 2 we keep checking till when our baseSum is less than n, if we get (n - baseSum) divisible by k we increase count by 1.

## Solution
```java
public int getCount(int n) {
        // code here
        int count = 0;
        long k = 2;
        while(true){
            long baseSum = (k*(k-1))/2;
            if(baseSum >= n)
                break;
            if((n - baseSum) % k == 0)
                ++count;
            k++;
        }
        return count;
    }