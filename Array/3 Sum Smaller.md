# 3 Sum Smaller   

Given an array of n integers nums and a target, find the number of index triplets `i, j, k` with `0 <= i < j < k < n` that satisfy the condition `nums[i] + nums[j] + nums[k] < target`.

For example, given `nums = [-2, 0, 1, 3]`, and target = `2`.

Return 2. Because there are two triplets which sums are less than 2:
```
[-2, 0, 1]
[-2, 0, 3]
```

```java
public int threeSumSmaller(int[] nums, int target) {
    
    // Sort array first
    Arrays.sort(nums);
    int n = nums.length;
    int res = 0;
    
    for (int i = 0; i < n; i++) {
    
        int j = i + 1;
        int k = n - 1;
        
        while (j < k) {
            int sum = nums[i] + nums[j] + nums[k];
            if (sum < target) {
                // As sorted, any number in between k and j 
                // will less than target.
                res += k - j;
                j++;
            } else {
                k--;
            }
        }
    }
    
    return res;
}
```