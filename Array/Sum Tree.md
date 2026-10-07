---
platform: GeeksforGeeks
difficulty: Medium
tags: [tree, binary-tree, recursion]
date_solved: 2026-09-29
---

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/sum-tree/1)
* **Difficulty:** Medium
* Time Complexity: O(n)
* Auxiliary Space: O(h)


## Approach

A node is a sum tree if the value of the current node equals the sum of the values of its left and right subtrees.

The best way to check this is with a post-order traversal:

1. Recurse on the left subtree.
2. Recurse on the right subtree.
3. If the current node is a leaf, return its value.
4. Otherwise, compute the sum of the left and right subtree totals.
5. If that sum equals the node's value, then this subtree is valid, and we return the total subtree sum as `leftSum + rightSum + node.data`.
6. If any subtree violates the condition, return `-1` to indicate failure.

This works because we evaluate children first and then validate the parent using the totals already computed. The recursion ensures each node is checked exactly once.

Time Complexity: O(n)
Auxiliary Space: O(h)

## Solution
```java
int isSumTreeHelper(Node root) {
    if (root == null)
        return 0;
    if (root.left == null && root.right == null)
        return root.data;
    int ls = isSumTreeHelper(root.left);
    if (ls == -1)
        return -1;
    int rs = isSumTreeHelper(root.right);
    if (rs == -1)
        return -1;
    if (ls + rs == root.data)
        return ls + rs + root.data;
    return -1;
}

boolean isSumTree(Node root) {
    return isSumTreeHelper(root) != -1;
}