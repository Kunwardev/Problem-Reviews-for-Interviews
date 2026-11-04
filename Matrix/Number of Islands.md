---
platform: Gemini
difficulty: Medium
tags:
  - BFS
  - DFS
  - matrix
date_solved: 2026-10-27
---

#  Problem Name

* **Problem Link:** [GeeksforGeeks Link](https://www.geeksforgeeks.org/dsa/find-the-number-of-islands-using-dfs/)
* **Difficulty:** Medium
* **Time Complexity:** $O(n*m)$
* **Space Complexity:** $O(n*m)$

## Approach
Whenever Land is encountered, Use BFS or DFS Traversal to count all the adjacent Lands and then make it a count++. 
DFS is deeper, So, in case of deeper rows and cols, the algo might fail, but not for BFS because it is one at a time using Queue
## Solution
```java
private static int function(int[][] matrix){

// If Matrix is null or if m and n are 0

if(matrix == null || matrix.length == 0)
return 0;
}

// Counting the Number of Islands
int count = 0;
for(int i=0;i<m;i++){
	for(int j=0;j<n;j++){

// If the 1 is already counted or if it is water

		if(matrix[i][j] == 2 || matrix[i][j] == 0)
			continue;

		else{
			count++;
			DFS(matrix, i, j, m, n);
		}
	}
}
return count;
}

private static void DFS(int[][] matrix, int i, int j, int m, int n) {
	matrix[i][j] = 2;
	int[] row = new int[]{1, -1, 0, 0};
	int[] col = new int[]{0, 0, 1, -1};
	for(int k=0;k<4;k++){
		if(i+row[k] >= 0 && i+row[k] < m &&j+col[k] >= 0 && j+col[k] < n){
			if(matrix[i+row[k]][j+col[k]] == 1)
				DFS(matrix, i+row[k], j+col[k], m, n);
			}
		}
	}
	
	
	
```

```java
public static boolean isSafe(char[][] grid, int r, int c, boolean[][] visited) {
        int n = grid.length;
        int m = grid[0].length;
        return (r >= 0 && r < n && c >= 0 && c < m && grid[r][c] == 'L' && !visited[r][c]);
    }

    public static void bfs(char[][] grid, boolean[][] visited, int startR, int startC) {
        
        // Possible 8 directions (vertical, horizontal, and diagonal)
        int[] dRow = {-1, -1, -1, 0, 0, 1, 1, 1};
        int[] dCol = {-1, 0, 1, -1, 1, -1, 0, 1};

        Queue<int[]> q = new LinkedList<>();
        q.add(new int[]{startR, startC});
        visited[startR][startC] = true;

        // Explore all reachable land cells for this island
        while (!q.isEmpty()) {
            int[] cell = q.poll();
            int r = cell[0];
            int c = cell[1];

            // Check all 8 neighbors of the current cell
            for (int k = 0; k < 8; k++) {
                int newR = r + dRow[k];
                int newC = c + dCol[k];
                if (isSafe(grid, newR, newC, visited)) {
                    visited[newR][newC] = true;
                    q.add(new int[]{newR, newC});
                }
            }
        }
    }

    // Count the total number of islands in the grid
    public static int countIslands(char[][] grid) {
        int n = grid.length;
        int m = grid[0].length;
        boolean[][] visited = new boolean[n][m];
        int islandCount = 0;

        // Traverse every cell in the grid
        for (int r = 0; r < n; r++) {
            for (int c = 0; c < m; c++) {

                // If an unvisited land cell is found, start BFS for that island
                if (grid[r][c] == 'L' && !visited[r][c]) {
                    bfs(grid, visited, r, c);
                    islandCount++;
                }
            }
        }

        return islandCount;
    }
```