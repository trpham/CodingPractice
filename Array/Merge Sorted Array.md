# Merge Sorted Array

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
    
    // Convert size to index
    int i = m - 1;
    int j = n - 1;
    int k = m + n - 1;
    
    while (i >= 0 && j >= 0) {
        
        int n1 = nums1[i];
        int n2 = nums2[j];
        
        if (n1 > n2) {
            nums1[k] = n1;
            i--;
        } else {
            nums1[k] = n2;
            j--;
        }

        k--;
    }
    
    // Copy the rest of nums2[j] over if any
    while (j >= 0) {
        nums1[k] = nums2[j];
        j--;
        k--;
    }
}
```

