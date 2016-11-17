# Integer Break

Given a positive integer n, break it into the sum of at least two positive integers and maximize the product of those integers. Return the maximum product you can get.

Note: You may assume that n is not less than 2 and not larger than 58.

**Ideas**:
- `n = 2` -> `1` `(2 = 1 + 1)`.

- `n = 10 -> 36` `(10 = 3 + 3 + 4)`.

- Can use DP

```java
public int integerBreak(int n) {

    // IB[i] is maximum product for break down i
    int[] IB = new int[n + 1];
    
    // IB[i] = Max (IB[i], Max(IB[j], j) * Max(IB[i-j], i-j))
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j < i; j++) {
            IB[i] = Math.max(IB[i], 
                    Math.max(IB[j], j) * Math.max(IB[i-j], i-j));
        }
    }

    return IB[n];
}

```