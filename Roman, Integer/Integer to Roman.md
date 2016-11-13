# Integer to Roman

Convert an integer to a roman numeral.

Input is within the range from 1 to 3999.

**Ideas**

- Make arrays for key:integer and value:roman, from big to small.
- The key is include special orientations such as CM (900), CD (400), XC (90)... in the arrays.
- Subtract the number by the roman letter range that it fits within.

```java
public String intToRoman(int num) {
    
    int[] k = new int[] {1000, 900, 500, 400, 100, 90, 
                         50, 40, 10, 9, 5, 4, 1};
    String[] v = new String[] {"M", "CM", "D", "CD", "C", "XC",
                               "L", "XL", "X", "IX", "V", "IV", "I"};
    
    StringBuilder res = new StringBuilder();
    
    for (int i = 0; i < k.length; i++) {
        while (num >= k[i]) {
            num -= k[i];
            res.append(v[i]);
        }
    }
    
    return res.toString();
}
```
