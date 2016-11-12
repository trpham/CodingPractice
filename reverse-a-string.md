# Reverse String 

Write a function that takes a string as input and returns the string reversed. 

**Example:** 

Given s = "hello", return "olleh". 

```java
public String reverseString (String s) {
    char[] arr = s.toCharArray();
    int l = 0; int r = s.length() - 1;
    while(l < r) { 
        char temp = cArray[l];
        cArray[l] = cArray[r];
        cArray[r] = temp; 
        l++; 
        r--; 
    } 
    return String.valueOf(arr); 
}
```
