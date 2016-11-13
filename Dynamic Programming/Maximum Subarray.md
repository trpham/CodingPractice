# Maximum Subarray

Find the contiguous subarray within an array (at least 1 number) which has the largest sum.

**Ideas**:

- `[-2,1,-3,4,-1,2,1,-5,4]` -> `[4,-1,2,1]` (largest sum = 6)
- Use dynamic programming
- `MS[0...i]` is the maximum subarray from index 0 to i (up and **including** i)
- `MS[0...i]` depends on the previous, `MS[1...i]`
- If `MS[0...i-1]` is positive -> include it: `MS[0...i] = MS[0...i-1] + A[i]`
- If `MS[0...1-i]` is negative -> ignore it: `MS[0...i] = A[i]`
- Base case: At index 0 -> `MS[0] = A[0]`

```java
public int maxSubArray(int[] A) {
    
    int n = A.length;
    
    int[] MS = new int[n];
    MS[0] = A[0];
   
    for (int i = 1; i < n; i++) {
        MS[i] = Math.max(MS[i-1] + A[i], A[i]);
    }
    
    // Find the largest sum in MS
    int max = MS[0];
    for (int i = 1; i < n; i++) {
        if (MS[i] > max) {
            max = MS[i];
        }
    }

    return max;
}
```