# Combination Sum II

Given a collection of numbers A and a target B, find all unique combinations in A which sums up to T.

Each number in C may only be used **once** in the combination.

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.

For example, given candidate set `[10, 1, 2, 7, 6, 1, 5]` and target `8` 

A solution set is: 
```
[1, 7],
[1, 2, 5],
[2, 6],
[1, 1, 6]

```

**Ideas**:
- DFS

```java
public List<List<Integer>> combinationSum2(int[] nums, int target) {
    
    // Sort to avoid duplicates
    Arrays.sort(nums);
    
    List <List<Integer>> res = new ArrayList<>();
    List <Integer> curr = new ArrayList<>();
    
    dfs(0, nums, target, curr, res);
    
    return res;
}

public void dfs(int start, int[] nums, int target,
    List <Integer> curr, List <List<Integer>> res) {

    if (target == 0) {
        res.add(new ArrayList<Integer>(curr));
        return;
    }
    
    // Call dfs on 'next' index, newTarget
    for (int i = start; i < nums.length; i++) {

        int num = nums[i];

        if (num > target) {
            return;
        }
        
        // A trick to avoid duplicates
        if (i == start || nums[i] != nums[i - 1]) {
            int newTarget = target - num;
            curr.add(num);     
            // DFS on i + 1 because duplicates are not allowed
            dfs(i + 1, nums, newTarget, curr, res);
            curr.remove(curr.size() - 1);
        }           
    }
}
```