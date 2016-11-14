# Word Break

Given a string s and a dictionary of words dict, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

**Ideas**:

s = "leetcode", dict = ["leet", "code"].

Return true because "leetcode" can be segmented as "leet code".

Dynamic Programming:
- Boolean array WB[i] = True -> string s[0...i] can be segmented. Otherwise, false. 
- WB[i] is only true when dictionary contains the WORD
 and WB[starting index of WORD is true. This will make sure the **whole** string will be segmented into dictionary words.
- Base case: WB[0] = true

```java
public boolean wordBreak(String s, Set<String> dict) {

    int n = s.length();

    // WB[i] is false by default
    boolean[] WB = new boolean[n + 1];
    WB[0] = true;

    for (int i = 1; i <= n; i++){
        for (int j = 0; j < i; j++){
            String t = s.substring(j, i);
            if (WB[j] && dict.contains(t)){
                WB[i] = true;
            }
        }
    }    

    return WB[n];
}


```
