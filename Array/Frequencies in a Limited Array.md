---
platform: GeeksforGeeks
difficulty: Easy
tags: [array, hashing]
date_solved: 2026-09-29
---

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/frequency-of-array-elements-1587115620/1)
* **Difficulty:** Easy
* **Time Complexity:** $O(n)$
* **Space Complexity:** $O(1)$

## Solution
```java
int length = arr.length;
for(int i=0; i<length; i++) {
    arr[i]--;
}
for(int i=0; i<length; i++) {
    int idx = arr[i] % length;
    arr[idx] += length;
}

List<Integer> result = new ArrayList<>(Arrays.asList(arr));

// replaced with above ( Can be deleted)
//for(int i=0; i<length; i++) {
//    arr[i] = arr[i] / length;
//    List<Integer> result = new ArrayList<>();
//    for(int i: arr)
//        result.add(i);
//}