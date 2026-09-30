---
platform: GeeksforGeeks
difficulty: Easy
tags:
  - array
  - hashing
date_solved: 2026-09-29
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/frequency-of-array-elements-1587115620/1)
* **Difficulty:** Easy
* **Time Complexity:** $O(n)$
* **Space Complexity:** $O(1)$

## Approach
Adding the length of the array in the index of the number that is present at that loop. Then loop again and divide by length to get the count. 

## Solution
```java
public int nonRepeatingCharacter(int arr[]) {
    int length = arr.length; 
    for(int i=0; i<length; i++) 
    { 
	    // TO MATCH IT WITH THE INDEX
	    arr[i]--; 
	} 
	for(int i=0; i<length; i++) 
	{ 
		int idx = arr[i] % length;
		arr[idx] += length; 
	} 
	for(int i=0; i<length; i++) 
	{ 
		arr[i] = arr[i] / length; 
		List<Integer> result = new ArrayList<>(); 
		for(int i: arr) result.add(i);
	}
	return result;
}