# Palindrome Number

Determine whether an integer is a palindrome. 

Do this without extra space.

**Ideas**:
Reverse the string and compare with the original

```java
public boolean isPalindrome(int x) {
    if (x < 0) {
        return false;
    }
    return x == reverse(x);
}

public int reverse(int x) {
    int y = 0;
    while(x > 0) {
        y = y * 10 + x % 10;
        x /= 10;
    }
    return y;
}
```

