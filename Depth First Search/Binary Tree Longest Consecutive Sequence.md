# Binary Tree Longest Consecutive Sequence

Given a binary tree, find the length of the longest consecutive sequence path.

The path refers to any sequence of nodes from some starting node to any node in the tree along the parent-child connections. 

The longest consecutive path need to be from parent to child (cannot be the reverse).

For example,
```
   1
    \
     3
    / \
   2   4
        \
         5
```
Longest consecutive sequence path is `3-4-5`, so return `3`.
```
   2
    \
     3
    / 
   2    
  / 
 1
```
Longest consecutive sequence path is `2-3`, not `3-2-1`, so return `2`.

```java
public class Solution {
    
    private int max = 0;
    
    public int longestConsecutive(TreeNode root) {
        if (root == null) {
            return 0;
        }
        
        dfs(root, 0, root.val);

        return max;
    }
    
    public void dfs(TreeNode root, int count, int target) {
        
        if (root == null) {
            return;
        }
        
        if (root.val == target) {
            count++;
        } else {
            count = 1;
        }
        
        max = Math.max(max, count);
        
        // Target is always equals root.val + 1 
        dfs(root.left, count, root.val + 1);
        dfs(root.right, count, root.val + 1);
    }
}
```