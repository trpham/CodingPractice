# Nim Game 
There is a heap of stones on the table, each time one of you 
take turns to remove 1 to 3 stones. The one who removes the 
last stone will be the winner. Both of you are very clever 
and have optimal strategies for the game. 

Write a function to determine whether you can win the game 
given the number of stones in the heap. 

**Example:** 

If there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend. 

```java
public boolean canWinNim(int n) {
    /* 
    If there's 4 stones in the heap, no matter I pick 1, 2 or 3 stones,
    the opponent will remove the 3, 2 or 1 stone(s) that leftover and win.
    If 5, 6 or 7, we can leave 4 stones to the opponent. 
    */ 
    return n % 4 != 0; 
} 
```
