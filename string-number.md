String Number

Given an array of integers, every element appears twice except for one. 
Find that single one.

Your algorithm should have a linear runtime complexity and extra memory.

** Example **
Given \[1,2,1\] -&gt; Return 2

```java

public int singleNumber(int[] nums) {

    // The key is XOR in binary: 1 ^ 0 = 0, 1 ^ 1 = 1; 0 ^ 0 = 1
    // [1, 3, 1] -> 1 ^ 3 ^ 1 
    // In binary: (0001 ^ 0011) ^ 0001 = 0010 ^ 0001 = 0001 = 3

    int result = 0;

    for(int i = 0; i < nums.length; i++) {
        result = result ^ nums[i];
    }

    return result;
}
```

