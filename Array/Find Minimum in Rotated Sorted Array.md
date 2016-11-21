# Find Minimum in Rotated Sorted Array

Suppose a sorted array is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Find the minimum element.

You may assume no duplicate exists in the array.

```java
public int findMin(int[] nums) {
    
    int l = 0;
    int r = nums.length - 1;
    
    while (l < r) {

        // If mid < right, the smallest should be in left...mid 
        // {4 1 2 3} -> 1 < 3 -> {4, 1}
        // If mid > right, the smallest should be in mid + 1... right 
        // {3 4 1 2} -> 4 2 -> {1 2}

        int mid = (l + r) / 2;
   
        if (nums[mid] < nums[r]) {
            r = mid;     
        } else {
            l = mid + 1;
        }
    }
    
    return nums[l];
}
```