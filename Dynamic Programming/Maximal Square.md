# Maximal Square

Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

For example, given the following matrix:
```
1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0
```

Return 4.

**Ideas**:


Version 1: Use `MS` size `[n + 1][m + 1]`, add dummy 0s to the top column and left row.

```java
public int maximalSquare(char[][] matrix) {

    if (matrix == null || matrix.length == 0 || matrix[0].length == 0) return 0;
    
    // MS[i][j] is maximal square at lower left [i][j]
    int n = matrix.length;
    int m = matrix[0].length;
    int[][] MS = new int[n + 1][m + 1];

    // MS[i][j] = Min(MS[i-1][j-1], MS[i-1][j], MS[i][j-1]) + 1;
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= m; j++) {

            // In matrix, index start 1 less
            if (matrix[i - 1][j - 1] == '1') {
                MS[i][j] = Math.min(MS[i-1][j-1], Math.min(MS[i-1][j], MS[i][j-1])) + 1;
            } else {
                MS[i][j] = 0;
            }
        }
    }

    // Find max element in MS
    int max = 0;
    for (int i = 0; i <= n; i++) {
        for (int j = 0; j <= m; j++) {
            if (MS[i][j] > max) {
                max = MS[i][j];
            }
        }
    }

    return max * max;
}

```

Version 2: Use `MS` size `[n][m]`, then fill the top row and first column first.

```java
public int maximalSquare(char[][] matrix) {

    if (matrix == null || matrix.length == 0 || matrix[0].length == 0) return 0;
    
    // MS[i][j] is maximal square at lower left [i][j]
    // Row: i -> n, Column: j -> n
    int n = matrix.length;
    int m = matrix[0].length;
    int[][] MS = new int[n][m];
    
    // Top Column
    for (int i = 0; i < n; i++) {
        MS[i][0] = Character.getNumericValue(matrix[i][0]);
    }
    
    // Left Row
    for (int j = 0; j < m; j++) {
        MS[0][j] = Character.getNumericValue(matrix[0][j]);
    }
    
    // MS[i][j] = Min(MS[i-1][j-1], MS[i-1][j], MS[i][j-1]) + 1;
    for (int i = 1; i < n; i++) {
        for (int j = 1; j < m; j++) {

            if (matrix[i][j] == '1') {
                MS[i][j] = Math.min(MS[i-1][j-1], 
                           Math.min(MS[i-1][j], MS[i][j-1])) + 1;
            } else {
                MS[i][j] = 0;
            }
        }
    }

    // Find max element in MS
    int max = 0;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            if (MS[i][j] > max) {
                max = MS[i][j];
            }
        }
    }

    return max * max;
}

```

