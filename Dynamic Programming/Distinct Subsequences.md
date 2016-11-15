# Distinct Subsequences

Given a string A and a string B, count the number of distinct subsequences of B in A.

A subsequence of a string is a new string which is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (ie, "ACE" is a subsequence of "ABCDE" while "AEC" is not).

**Ideas**:

- A = "rabbbit", B = "rabbit" -> 3 (The only differece is 'bbb' vs 'bb', and there are 3 way of picking 2 out 3 b in 'bbb' to get 'bb')

Dynamic programming bottom-up:

- DS[i][j] is number of subsequences in A[0..i] equals B[0...j]


- If A[i] = B[j], we can check on either both A[i-1], B[j-1] or only B[j-1] (stay on A[i]), whichever is larger

    `A[i] == B[j], DS[i][j] = DS[i-1][j] + DS[i-1][j-1]`

- If A[i] != B[j], then the only option is checking on B[j-1]. Can not leave A[i] to A[i-1] because we haven't find a match for that i-th element yet.
    
    `DS[i][j] = DS[i-1][j]`

- Base case: 
    
    There is 0 subsequence if A is empty: 
    
    `DS[0][j] = 0`

    Always have 1 (which is empty) subsequence in A if B is empty: 
    
    `DS[i][0] = 1`


```java
public int numDistinct(String A, String B) {
    
    int n = A.length();
    int m = B.length();
    int[][] DS = new int[n + 1][m + 1];
    
    for (int j = 0; j <= m; j++) {
        DS[0][j] = 0;
    }
    
    for (int i = 0; i <= n; i++) {
        DS[i][0] = 1;
    }
    
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= m; j++) {
            if (A.charAt(i-1) == B.charAt(j-1)) {
                DS[i][j] = DS[i-1][j] + DS[i-1][j-1];
            } else {
                DS[i][j] = DS[i-1][j];
            }
        }
    }

    return DS[n][m];
}


```