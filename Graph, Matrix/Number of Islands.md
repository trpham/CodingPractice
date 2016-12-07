# Number of Islands

Given a 2D grid of `'1'` (land) and `'0'` (water), count the number of islands ('1s' neighborhood).  You may assume all four edges of the grid are all surrounded by water.

**Ideas**:

- If find a `1`, count it, set it to `0`, and explore its neighbors (up, down, left, right). All of its neighbors with `1` will set to `0`. 
- This will make sure a `1s` neighborhood only get counted once.

```java
public int numIslands(char[][] grid) {

    int res = 0;

    for (int i = 0; i < grid.length; i++) {
        for (int j = 0; j < grid[0].length; j++) {
            if (grid[i][j] == '1') {
                res += 1;
                explore(grid, i, j);
            }
        }
    }

    return res;
}

public void explore(char[][] grid, int r, int c) {

    if (r < 0 || c < 0 || r >= grid.length || c >= grid[0].length) {
        return;
    }

    if (grid[r][c] == '1') {
        grid[r][c] = '0';
        explore(grid, r, c - 1);
        explore(grid, r, c + 1);
        explore(grid, r + 1, c);
        explore(grid, r - 1, c);
    }
}
```