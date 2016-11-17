# Coin Change

You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin

**Ideas**:
- coins = `[1, 2, 5]`, amount = 11 -> return 3 `(11 = 5 + 5 + 1).`

- coins = `[2]`, amount = 3 -> return -1 (not possible).

- DP Knapsack with repetition.

- CC[m] is the minimum coins needed to get ammount m.

- Base case: Initialize `CC[i]` to Infinity, since we don't know either it's possible or not. 

- Base case: `CC[0] = 0`, don't need any coins to get 0 amount.

- `CC[i]` is either itself, or `1  + CC[i - coin]` if there is a coin closet to amount i, whichever is smaller.

- `CC[i] = min(CC[i], CC[i - coin] + 1).`

```java
public int coinChange(int[] coins, int m) {
    
    int[] CC = new int[m + 1];
    
    for(int i = 0; i <= m; i++) {
        CC[i] = Integer.MAX_VALUE - 1;
    }

    CC[0] = 0;

    for (int i = 1; i <= m; i++) {
        for (int j = 0; j < coins.length; j++) {
            if (i >= coins[j]) {
                CC[i] = Math.min(CC[i], CC[i - coins[j]] + 1);
            }
        }
    }

    // Return CC[m]
    if (CC[m] == Integer.MAX_VALUE - 1) {
        return - 1;
    } else {
        return CC[m];
    }
}

```