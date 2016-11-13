# Reverse Integer

Reverse digits of an integer.

**Ideas**:
- 123 -> 321
- -123 -> -321
- LOOP: `reverse = x % 10 + reverse * 10`; `x = x / 10`
- No need to check for sign

```java
public int reverse(int x) {
    
    // Use long, and later convert to int to avoid overflow
    long y = 0;
        
    while (x != 0) {
        y = x % 10 + y * 10;
        x = x / 10;
    }
    
    if (y < Integer.MIN_VALUE || y > Integer.MAX_VALUE) {
        return 0;
    }
    
    return (int) y;
}
```