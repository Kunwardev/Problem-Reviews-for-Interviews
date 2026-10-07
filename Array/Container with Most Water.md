---
platform: Leetcode
difficulty: Medium
tags:
  - array
  - greedy
  - two-pointers
date_solved: 2026-10-07
---

* **Problem Link:** [LeetCode Link]()
* **Difficulty:** Medium
* **Time Complexity:** $O(n)$
* **Space Complexity:** $O(1)$

## Approach
Start a pointer from left and right. 
Now find the minimum of this and calculate the area by multiplying it with their distance ( right - left )
Compare it with MaxValue. 
One left > right, the loop is done, and answer will be present. 

## Solution
```java
public int maxArea(int[] height) {
    
        int left = 0, right = height.length-1, maxVolume = 0;
        while(left < right){
            maxVolume = Math.max(maxVolume, Math.min(height[left], height[right]) * (right - left));
            if(height[left] < height[right])
                left++;
            else
                right--;
        }
        return maxVolume;
    }