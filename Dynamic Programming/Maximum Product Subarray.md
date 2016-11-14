# Maximum Product Subarray

Find the contiguous subarray within an array (containing at least one number) which has the largest product.

**Ideas**:
- `[2,3,-2,4]` -> the contiguous subarray `[2,3]` with largest product = `6`.
- For product, both `"+"` and `"-"` matter
- `MAX[i]` is maximum product in `A[0...i]` (up and **including** i)
- `MIN[i]` is minimum product (consider negative case)
- If previsou `max > 0` and `A[i] > 0` -> `A[i] * MAX[i - 1]`
- If previous `min < 0` and `A[i] < 0` -> `A[i] * MIN[i - 1]`
- Formula: `MAX[i] = Max(A[i], A[i]*MAX[i-1], A[i]*MIN[i-1])`
- Calculate `MIN[i]` as a helper for `MAX[i]`


```java
public int maxProduct(int[] A) {

    int n = A.length;
    int[] Max = new int[n];
    int[] Min = new int[n];
    
    Max[0] = A[0];
    Min[0] = A[0];
    
    for (int i = 1; i < n; i++) {
        Max[i] = Math.max(A[i], Math.max(A[i]*Max[i-1], A[i]*Min[i-1]));
        Min[i] = Math.min(A[i], Math.min(A[i]*Max[i-1], A[i]*Min[i-1]));
    }
    
    // Find max element in MAX
    int max = Max[0];
    for (int i = 0; i < n; i++) {
        if (Max[i] > max) {
            max = Max[i];
        }
    }

    return max;
}

```
