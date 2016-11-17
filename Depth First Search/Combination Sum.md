# Combination Sum

Given a set of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The same repeated number may be chosen from C unlimited number of times.

Note:
All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.


**Ideas**:

- `[2, 3, 6, 7]` and target `7` -> solution set is: `{[7],[2, 2, 3]}`
- Use DFS between set1 `[2,3,6,7]` and set2 `[7]` until set2 runout.
- Number can be **repeated**

```java
public List <List<Integer>> combinationSum(int[] nums, int target) {

    List <List<Integer>> res = new ArrayList<>();
    List <Integer> curr = new ArrayList<>();

    dfs(0, nums, target, curr, res);

    return res;
}

public void dfs(int start, int[] nums, int target, 
    List<Integer> curr, List<List<Integer>> res) {
    
    if (target == 0) {
        res.add(new ArrayList<Integer>(curr));
        return;
    } 

    for (int i = start; i < nums.length; i++) {
        
        int num = nums[i];
    
        if (num <= target) {
            int newTarget = target - num;
            curr.add(num);
            // Call DFS on i (not i+1) because repeated number is allowed
            dfs(i, nums, newTarget, curr, res);
            curr.remove(curr.size() - 1);
        }
    }
}
```