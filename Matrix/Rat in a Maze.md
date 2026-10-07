---
platform: GeeksforGeeks
difficulty: Medium
tags: [backtracking, recursion, matrix]
date_solved: 2026-09-29
---

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)
* **Difficulty:** Medium
* Time Complexity: O(4 ^ (n * n))
* Auxiliary Space: O(n * n)

## Approach

We need to find all valid paths from the top-left corner to the bottom-right corner in a maze, moving only in four directions: down, left, right, and up.

A standard approach is backtracking:

1. Start from `(0, 0)` and mark it as visited.
2. Try all four possible moves from the current cell if the next cell is inside the grid, is open (`1`), and has not been visited.
3. Append the corresponding direction to the path string and recursively continue.
4. When we reach the destination `(n-1, n-1)`, store the path as a valid answer.
5. Backtrack by unmarking the cell so other routes can be explored.

This explores all possible valid routes while avoiding cycles and revisiting cells.

Time Complexity: O(4^(n*n)) in the worst case, because each cell can branch into up to 4 moves.
Auxiliary Space: O(n*n) for the visited matrix and recursion stack.

## Solution
```java
public ArrayList<String> ratInMaze(int[][] maze) {
    boolean[][] visited = new boolean[maze.length][maze.length];
    ArrayList<String> result = new ArrayList<>();
    if(maze[0][0] == 1) {
        ratInMazeBacktrack(maze, maze.length, 0, 0, "", visited, result);
    }
    Collections.sort(result);
    return result;
}

private void ratInMazeBacktrack(int[][] maze, int n, int i, int j, String path, boolean[][] visited, ArrayList<String> res) {
    int[] rD = new int[]{1, 0, 0, -1};
    int[] cD = new int[]{0, -1, 1, 0};
    char[] sD = new char[]{'D','L','R','U'};
    
    if(i == n - 1 && j == n - 1){
        res.add(path);
        return;
    }
    visited[i][j] = true;
    for(int k=0; k<4; k++){
        int nx = i + rD[k], ny = j + cD[k];
        if(nx >= 0 && nx < n && ny >= 0 && ny < n && maze[nx][ny] == 1 && !visited[nx][ny]){
            ratInMazeBacktrack(maze, n, nx, ny, path + sD[k], visited, res);
        }
    }
    visited[i][j] = false;
}