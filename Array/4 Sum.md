# 4 Sum

Given an array S of n integers, are there elements a, b, c, and d in S such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.

Note: The solution set must not contain duplicate quadruplets.

For example, given array `S = [1, 0, -1, 0, -2, 2]`, and target = `0`.
 
A solution set is: 
```
[-1, 0, 0, 1], 
[-2, -1, 1, 2], 
[-2, 0, 0, 2] 
```
```java
public List <List<Integer>> fourSum(int[] nums, int target) {
    
    Arrays.sort(nums);
    int n = nums.length;  
    List <List<Integer>> res = new LinkedList<>();
    
    for (int i = 0; i < n - 3; i++) {
        
        // Avoid duplicates
        if (i > 0 && nums[i] == nums[i - 1]) {
            continue;
        }
        
        for (int j = i + 1; j < n - 2; j++) {
            
            if (j > i + 1 && nums[j] == nums[j - 1]) {
                continue;
            }
            
            int l = j + 1;
            int r = n - 1;
            
            while (l < r) {
                
                int sum = nums[i] + nums[j] + nums[l] + nums[r];
                
                if (sum == target) {
                    List <Integer> list =
                    Arrays.asList(nums[i], nums[j], nums[l], nums[r]);
                    res.add(list);
                    
                    // Don't count me again if a version of me 
                    // (either l or r) has made it to the sum
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
                    
                } else if (sum > target) {
                    r--;
                } else {
                    l++;
                }
            }
        }
    }
    
    return res;
}
```

