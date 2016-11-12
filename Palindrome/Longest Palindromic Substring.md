# Longest Palindromic Substring

Find the longest palindromic substring in string s. Assume that the maximum length of s is 1000.

**Ideas**:
- "babad" -> "bab"
- "cbbd" -> "bb"

Expansion from the inside and keep track of the left and right pointers.

```java
public class Solution {
    
    private int l = 0;
    private int r = 0;

    public String longestPalindrome(String s) {
        int n = s.length();
        for (int i = 0; i < n; i++) {
            // The Substring can be odd or even ('aba' or 'abba')        
            palindrome(s, i, i);
            palindrome(s, i, i + 1);
        }    
        return s.substring(l, r + 1);
    }

    public void palindrome(String s, int l1, int r1) {    
        while (l1 >= 0 && r1 < s.length() 
                       && s.charAt(l1) == s.charAt(r1)) {
            l1--;
            r1++;
        }
        // Narrow down L1 and R1 one step each, because they do 
        // extra expansion just right before escaped the while loop
        l1++;
        r1--;
      
        int curMaxLen = r - l + 1;        
        int len = r1 - l1 + 1;
        if (len > curMaxLen) {
            l = l1;           
            r = r1;
        }
    }
}
```