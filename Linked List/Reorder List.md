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
public static ListNode reorder(ListNode head)

{

ListNode slow = head;
ListNode fast = head.next;

while(fast != null && fast.next != null){

slow = slow.next;
fast = fast.next.next;
}

ListNode divide = slow.next;
slow.next = null;
divide = reverse(divide);
ListNode temp = head;

while(temp != null && divide != null){
System.out.print(temp.val + " ");
System.out.print(divide.val+" ");
temp = temp.next;
divide = divide.next;

}

if(temp != null){

System.out.print(temp.val);
temp = temp.next;
}
return null;
}

  

private static ListNode reverse(ListNode divide) {

ListNode current = divide;
ListNode prev = null, next;
while(current != null){
next = current.next;
current.next = prev;
prev = current;
current = next;
}
return prev;
}