# Two Sum

Given an array of integers, return indices of the two numbers that sum up to a target.

Assume that each input would have exactly **one** solution.

**Example:**

* Given nums = `[2, 7, 11, 15]`, target = `9`
* Result is array `[0, 1]` because `nums[0] + nums[1]` = `2 + 7` = `9`

```java
public int[] twoSum(int[] nums, int target) {

    Map <Integer, Integer> map = new HashMap<>();

    int n = nums.length;

    for (int i = 0; i < n; i++) {
        if (map.containsKey(nums[i])) {
            return new int[] {map.get(nums[i]), i};
        } else { 
            map.put(target - nums[i], i); 
        } 
    } 

    return new int[]{0,0}; 
}
```
