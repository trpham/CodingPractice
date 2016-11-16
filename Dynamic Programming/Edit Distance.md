# Edit Distance

Given two words word1 and word2, find the minimum number of steps required to convert word1 to word2. (each operation is counted as 1 step.)

You have the following 3 operations permitted on a word:

a) Insert a character

b) Delete a character

c) Replace a character

**Ideas**:
-  `ED[i, j]` is minimum edit steps for word1 (0...i) and word2 (0...j). 

- As matrix ED has size [n + 1][m + 1], rows of ED will go from 0 to n with array size n + 1, likewise columns will go from 0 to m with size m + 1. However, indices in word1, as usual, goes from 0 to n - 1 (size n), and in word2 goes from 0 to m - 1 (size m). This trick (one extra element) is common in 2D array DP problems.

- `ED[i, 0] = i`, when word2 is empty, min step is i

- Smaller both indices and check on the characters at i and j to see if we need none (they are same) or 1 edit (they are different) -> `ED[i-1, j-1] + diff(i,j)`

- Or if the element at i, j are different, test with smaller index of either dimension -> `ED[i-1,j] + 1, ED[i,j-1] + 1`

- `ED[i, j] = Min[ ED[i-1, j-1] + diff(i,j), ED[i-1,j] + 1, ED[i,j-1] + 1)]`

```java
public int minDistance(String word1, String word2) {
 
    int n = word1.length();
    int m = word2.length();

    int[][] ED = new int[n + 1][m + 1];
    
    char[] w1 = word1.toCharArray();
    char[] w2 = word2.toCharArray();
    
    for (int i = 0; i <= n; i++) {
        ED[i][0] = i;
    }

    for (int j = 0; j <= m; j++) {
        ED[0][j] = j;
    }
    
    int dif = 0;
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= m; j++) {
            
            // i from 1 to N, likewse j from 1 to M
            // But in such array as W1, index goes from 0 to N-1
            if (w1[i - 1] == w2[j - 1]) {
                dif = 0;
            } else {
                dif = 1;
            }
            
            ED[i][j] = Math.min(ED[i-1][j-1] + dif,
                       Math.min(ED[i][j-1] + 1, ED[i-1][j] + 1));
        }
    }
    
    return ED[n][m];
}

```