# Minimum Path Sum

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

**Ideas**:
- `MPS[i, j]` is minimum sum along the path from `[0][0] to [i - 1][j - 1]` (i, j are matrix indices)

- Row: i -> n, Column: j -> m

- MPS at `[i][j]` is the sum of value at `[i][j]` with either the above or left neighbor MSP, whichever is smaller.

- `MPS[i][j] = min(MPS[i][j-1] + grid[i][j], MPS[i-1][j] + grid[i][j])`

- We often do not define MPS with size `[n + 1][m + 1]` in matrix related problems like this one, because we will get NullException while trying to retrive the values at index n and m.

- Base cases: Top row and left column, each is one path, then sum them up


```java
public int minPathSum(int[][] grid) {
    
    int n = grid.length;
    int m = grid[0].length;
    int[][] MPS = new int[n][m];
      
    // Top row
    for (int j = 1; j < m; j++) {
        MPS[0][j] = grid[0][j] + MPS[0][j - 1];
    }

    // Left column
    for (int i = 1; i < n; i++) {
        MPS[i][0] = grid[i][0] + MPS[i - 1][0];
    }
    
    for (int i = 1; i < n; i++) {
        for (int j = 1; j < m; j++) {
            MPS[i][j] = Math.min(MPS[i][j - 1] + grid[i][j],
                                 MPS[i - 1][j] + grid[i][j]);
        }
    }
    
    return MPS[n - 1][m - 1];
}

```