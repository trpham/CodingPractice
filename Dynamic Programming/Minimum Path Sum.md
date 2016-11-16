# Minimum Path Sum

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

**Ideas**:
- MPS[i, j] is mimized sum along path from [0][0] to [i][j]
- Row: i -> n, Column: j -> m

```java
public int minPathSum(int[][] grid) {
    
    int n = grid.length;
    int m = grid[0].length;
    int[][] MPS = new int[n][m];
    
    // Top Row is only one path -> sum them up
    for (int j = 1; j < m; j++) {
        MPS[0][j] = grid[0][j] + MPS[0][j - 1];
    }
    
    // Left column is only one paht -> sum them up
    for (int i = 1; i < n; i++) {
        MPS[i][0] = grid[i][0] + MPS[i - 1][0];
    }
    
    // MPS[i][j] = Math.min(MPS[i][j - 1] + grid[i][j], MPS[i - 1][j] + grid[i][j])
    for (int i = 1; i < n; i++) {
        for (int j = 1; j < m; j++) {
            MPS[i][j] = Math.min(MPS[i][j - 1] + grid[i][j],
                                 MPS[i - 1][j] + grid[i][j]);
        }
    }
    
    return MPS[n - 1][m - 1];
}

```