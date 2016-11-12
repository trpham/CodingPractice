# Longest Substring Without Repeating Characters

Find the length of the longest substring without repeating characters.

**Ideas**:

- Given "**abc**abcbb", the length is 3 ("abc")
- Given "**b**bbbb", the length is 1 ("b")
- Given "pw**wke**w", the length is 3 ("wke")

The answer must be a substring, "pwke" is a subsequence, not a substring.

Use a HashMap to keep track of each character and its **current** index (which is R). 

Check the occurrance of each character to move left pointer L and right pointer R, then calculate current length (= R - L + 1) as we traverse the string.

```java
public int lengthOfLongestSubstring(String s) { 
    
    int l = 0;
    int res = 0;

    Map<Character, Integer> map = new HashMap<>();

    for (int r = 0; r < s.length(); r++) {
        char c = s.charAt(r);
        if (!map.containsKey(c)) {
            map.put(c, r); 
        } else { 
            // Need MAX in such cases: 'abba', 'abac'
            // Skip the old location of char c, and go one step forward,  
            // or keep the location in L pointer because it's 
            // already far ahead, whichever is larger
            l = Math.max(l, map.get(c) + 1); 
            map.remove(c);
            map.put(c, r); 
        } 
        // Routinely checking on length, +1 because res is length, not index
        res = Math.max(res, r - l + 1); 
    } 

    return res; 
}
```
