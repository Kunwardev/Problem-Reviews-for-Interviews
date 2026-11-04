---
platform: Gemini
difficulty: Medium
tags:
  - sliding-window
  - string
date_solved: 2026-10-28
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/dsa/length-of-the-longest-substring-without-repeating-characters/)
* **Difficulty:** Medium
* **Time Complexity:** $O(n)$
* **Space Complexity:** $O(1)$

## Approach
using sliding window and creating a hash set that will contain if the character is repeated again or not

## Solution
```java
private static int function(String s){

	int maxLength = 0;
	int left = 0;
	HashSet<Character> presenCharacters = new HashSet<>();
	for(char current: s.toCharArray()){
		while (presenCharacters.contains(current)) {
			presenCharacters.remove(s.charAt(left++));
		}
	
		presenCharacters.add(current);
		maxLength = Math.max(maxLength, presenCharacters.size());
	}

	return maxLength;
}