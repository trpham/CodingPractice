# Minimum Depth of Binary Tree

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

Solution 1: Recursive

```java
public int minDepth(Node root) {
    
    if (root == null) return 0;
    
    // Consider the tree has only one element {1}
    // Don't need to check?
    if (root.left == null) {
        return minDepth(root.right) + 1;
    }

    if (root.right == null) {
        return minDepth(root.left) + 1;
    }
    
    return Math.min(minDepth(root.right), 
                    minDepth(root.left)) + 1;
}

```

Solution 2: BFS

```java
public int minDepth(Node root) {
    
    if (root == null) {
        return 0;
    }
    
    int res = 0;

    List<Node> nodes = new ArrayList<>();
    nodes.add(root);
    
    while (!nodes.isEmpty()) {

        res += 1;

        List<TreeNode> curr = nodes;

        nodes = new ArrayList<>();

        for (Node n : curr) {
            if (n.left == null && n.right == null) {
                return res;
            }

            if (n.left != null) {
                nodes.add(n.left);
            }

            if (n.right != null) {
                nodes.add(n.right);
            }
        }
    }

    return res;
}

```