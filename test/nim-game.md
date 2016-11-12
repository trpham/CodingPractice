# Nim Game 
There is a heap of stones, each person takes turns to remove 1 to 3 stones. The winner is the one who removes the last stone.

Determine whether you can win the game given the number of stones in the heap. 

**Ideas:** 

If there are 4 stones in the heap, no matter I pick 1, 2 or 3 stones, the opponent will remove the leftover 3, 2 or 1 stone(s) and win. If there are 5, 6 or 7 stones, I can pick 1, 2 or 3 and leave the opponent with 4 stones. In general, the idea is forcing **4n** stones to the opponent.

```java
public boolean canWinNim(int n) {
    return n % 4 != 0; 
} 
```
