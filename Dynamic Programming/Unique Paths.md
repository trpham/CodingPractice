# Unique Paths

A robot is located at the top-left corner of a m x n grid.

The robot can only move either **down** or **right** at any point in time. The robot is trying to reach the bottom-right corner of the grid.

How many possible unique paths are there?

**Ideas**:
- MPS[i, j] is number of paths from [0][0] to [i - 1][j - 1] (i, j are indices)
- Row: i -> n, Column: j -> m
- MPS[i][j] depends on its up and left neighbors.
- `MPS[i][j] = MPS[i][j - 1] + MPS[i - 1][j]`
- Base case: There is only one path on the top row and left column
- We not define MPS with size [n + 1][m + 1] because we are not comparing 2 strings, or in need of that extra 0s row/column spaces.

```java
public int uniquePaths(int n, int m) {

    int[][] MPS = new int[n][m];
    
    // Top Row
    for (int j = 0; j < m; j++) {
        MPS[0][j] = 1;
    }
    
    // Left column
    for (int i = 0; i < n; i++) {
        MPS[i][0] = 1;
    }
    
    for (int i = 1; i < n; i++) {
        for (int j = 1; j < m; j++) {
            MPS[i][j] = MPS[i][j - 1] + MPS[i - 1][j];
        }
    }
    return MPS[n - 1][m - 1];
}

```
