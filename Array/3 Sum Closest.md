# 3 Sum Closet

**Ideas**:
- For example, given array S = {-1 2 1 -4}, and target = 1.
- The sum that is closest to the target is 2 (-1 + 2 + 1 = 2).
- Similar to 3 Sum.

```java
public int threeSumClosest(int[] nums, int target) {

    Arrays.sort(nums);
    int n = nums.length;
    int res = nums[0] + nums[1] + nums[2];
    
    for (int i = 0; i < n; i++) {

        if (i > 0 && nums[i] == nums[i - 1]) {
            continue;
        }
        
        int l = i + 1;
        int r = n - 1;
        
        while (l < r) {

            int sum = nums[i] + nums[l] + nums[r];
            int currDif = Math.abs(sum - target);
            int resDif = Math.abs(res - target);
            
            if (currDif < resDif) {
                res = sum;
            }
            
            if (sum == target) {
                return sum;
            } else if (sum > target) {
                r--;
            } else {
                l++;
            }
        }
    }

    return res;
}
```