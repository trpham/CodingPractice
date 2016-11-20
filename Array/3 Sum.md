# 3 Sum

Given an array S, are there elements a, b, c in S such that a + b + c = 0? 

Find all unique triplets in the array which gives the sum of zero.


**Ideas**:
- For example, given array S = [-1, 0, 1, 2, -1, -4],
- A solution set is:`[[-1, 0, 1],[-1, -1, 2]]`
- Sort the array
- Use 3 pointers

```java
public List<List<Integer>> threeSum(int[] nums) {
    
    Arrays.sort(nums);
    int n = nums.length;
    List <List<Integer>> res = new ArrayList<>();
    
    for (int i = 0; i < n; i++) {        
        // To avoid cases such as [1,1,1...]
        if (i > 0 && nums[i] == nums[i - 1]) {
            continue;
        }

        int l = i + 1;
        int r = n - 1;

        while (l < r) {
            int sum = nums[i] + nums[l] + nums[r];
            if (sum == 0) {
                res.add(Arrays.asList(nums[i], nums[l], nums[r]));
                // Narrow down range l-r by eliminate duplicates
                while (l < r) {
                    if (nums[l] == nums[l + 1]) {
                        l++;
                    } else if (nums[r] == nums[r - 1]) {
                        r--;
                    } else {
                        break;
                    }
                }
                l++;
                r--;
            // Adjust left or right pointers depends on sum
            } else if (sum > 0) {
                r--;
            } else {
                l++;
            }
        }
    }
    
    return res;
}
```