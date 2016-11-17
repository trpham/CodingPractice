# Longest Increasing Subsequence

Given an unsorted array of integers, find the length of longest increasing subsequence.

**Ideas**:

- `[10, 9, 2, 5, 3, 7, 101, 18]` -> `[2, 3, 7, 101]`, therefore the length is 4. 

- Note that there may be more than one LIS combination, it is only necessary for you to return the length.

- Your algorithm should run in `O(n^2)` complexity.
- `LIS[i]` is the length of longest increasing subsequence from `0`...`i-1`

```java
public int lengthOfLIS(int[] nums) {
    
    int n = nums.length;
    int res = 0;

    int[] LIS = new int[n];
    
    // Initialize LIS to 1 (for any i, LIS[i] is least 1)
    for (int i = 0; i < n; i++) {
        LIS[i] = 1;
    }
    
    // If nums[i] > nums[j]:
    // LIS[i] = Max (LIS[i], LIS[j] + 1)
    for (int i = 1; i < n; i++) {
        for (int j = 0; j < i; j++) {
            if (nums[i] > nums[j]) {
                LIS[i] = Math.max(LIS[i], LIS[j] + 1);
            }
        }
    }
    
    // Return max from LIS
    for (int i = 0; i < n; i++) {
        if (LIS[i] > result) {
            res = LIS[i];
        }
    }

    return res;
}

```