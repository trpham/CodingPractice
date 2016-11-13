# Roman to Integer

Convert a Roman numeral to an integer.

Input in range 1 - 3999

**Ideas**:

Travese backward, and either add or substract each character's Roman value from the result.

Checking on with **natural orientation in a Roman number** (high to low): M D C L X V I. 

Reading right to left:
- **X**V -> **+10** + 5 = 15 (natural)
- **V**X -> **-5** + 10 = 5 (unnatural)

```java
public int romanToInt(String s) {

    Map<Character, Integer> map = new HashMap<>();
    map.put('I', 1);
    map.put('V', 5);
    map.put('X', 10);
    map.put('L', 50);
    map.put('C', 100);
    map.put('D', 500);
    map.put('M', 1000);
    
    char[] arr = s.toCharArray();
    // Index of last element, faster than using: arr.length - 1
    int i = s.length() - 1;   
    int res = map.get(arr[i]);
    
    // +/-v1 at i depends on the right neighbor v2 at i + 1
    for (i = i - 1; i >= 0; i--) {
        int v1 = map.get(arr[i]);
        int v2 = map.get(arr[i + 1]);
        if (v1 >= v2) {
            res += v1;
        } else {
            res -= v1;
        }
    }

    return res;
}
```
