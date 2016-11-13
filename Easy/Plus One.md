# Plus One

Given a non-negative number represented as an array of digits, plus one to the number.

The digits are stored such that the most significant digit is at the head of the list.

**Ideas**:
- [1,2,3] -> [1,2,4]
- [9,9,9] -> [1,0,0,0]

It's only the case either the number is XYZ or 999


```java
public int[] plusOne(int[] digits) {
    
    int n = digits.length;
    int i = n - 1;
    
    while(i >= 0) {
        if (digits[i] < 9) {     // Case XYZ
            digits[i]++;
            return digits;
        } else {                 // Case 999
            digits[i] = 0;    
        }    
        i--;
    }

    // New array with size n + 1 with first element = 1
    // It has to be the 999 case, otherwise, it's been returned as above
    int[] res = new int[n + 1];
    res[0] = 1;

    return res;
}
```
