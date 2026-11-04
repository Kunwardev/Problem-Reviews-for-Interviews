---
platform: Gemini
difficulty: Medium
tags:
  - backtracking
  - recursion
  - string
date_solved: 2026-11-03
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link]()
* **Difficulty:** Medium
* **Time Complexity:** $O(n4^n)$
* **Space Complexity:** $O(n4^n)$

## Approach
I am thinking of making HashMap with Character, List of Alphabets.

Now, I will start at the index 0, then take the first character of the list it points to, and then using recursion go to the next index, and keep on doing that until I have reached the end and exhausted all the permutations of the characters.

## Solution
```java
private static List<String> function(String message){
	List<String> result = new ArrayList<>();
	if(message == null || message.isEmpty())
		return result;

	HashMap<Character, String> dictionary = new HashMap();
	dictionary.put('2', "abc");
	dictionary.put('3', "def");
	dictionary.put('4', "ghi");
	dictionary.put('5', "jkl");
	dictionary.put('6', "mno");
	dictionary.put('7', "pqrs");
	dictionary.put('8', "tuv");
	dictionary.put('9', "wxyz");

	functionHelper(message, "", dictionary, 0, result);
	return result;
}

  

private static void functionHelper(String message, String tempMessage, HashMap<Character,String> dictionary, int index, List<String> result) 
{
if(index == message.length()){
	result.add(tempMessage);
	return;
}

	for(int i=0;i<dictionary.get(message.charAt(index)).length();i++){
		char tempLetter = dictionary.get(message.charAt(index)).charAt(i);
		functionHelper(message, tempMessage+tempLetter, dictionary, index+1, result);
	}
}