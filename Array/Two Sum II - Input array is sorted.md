# Two Sum II - Input array is sorted

Given an array of integers that is already sorted in **ascending order**, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. 

Please note that your returned answers (both index1 and index2) are **not zero-based**.

You may assume that each input would have exactly one solution.



**Ideas**:
- Numbers =`[2, 7, 11, 15]`, target =`9` -> indices `[1, 2]`
- Use 2 pointers
- It seems binary search is not sufficient for this problem

```java
public int[] twoSum(int[] nums, int target) {
    
    // Use 2 pointers
    int i = 0;
    int j = nums.length - 1;

    int[] res = new int[] {-1, -1};
    
    while (i < j) {

        int n1 = nums[i];
        int n2 = nums[j];
        int sum = n1 + n2;
        
        if (sum == target) {
            // Returned indices are not zero-based
            return new int[] {i + 1, j + 1};
        } else if (sum > target) {
            j--;
        } else {
            i++;
        }
    }
    
    return res;
}

```

