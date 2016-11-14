# Pow (x,n)

Implement pow(x, n).

**Ideas**:

When n is even, cut n in half and power up x (becomes x*x) 

When n is odd, remove 1 power by multiply x to result;
 - `3^4 = 3*3*3*3 -> res = 1*9*9`
 - `3^5 = 3*3*3*3*3 -> res = 1*3*9*9`

This way will reduce lots of multiplication as n will decay very fast.


```java
public double myPow(double x, int n) {
    // Corner cases on LeetCode testsuite
    if (n == Integer.MIN_VALUE) {
        if (x < 0) {
            return -1 / pow(x, Integer.MAX_VALUE);
        } else {
            return 1 / pow(x, Integer.MAX_VALUE);
        }
    }
    // Negative or positive power
    if (n < 0) {
        return 1 / pow(x, -n);
    } else {
        return pow(x, n);
    }
}

public double pow(double x, int n) {
    double res = 1;
    while(n > 0) {
        // Res will get updated at this condition check
        // It will hit at least once (when n becomes 1)
        if (n % 2 != 0) {
            res = res * x;
        } 
        x = x * x;
        n = n / 2;
    }
    return res;
}
```