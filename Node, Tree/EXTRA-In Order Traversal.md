# In Order Traversal

We print the leftmost grandchild first, then its parent and then same logic for its right sibling.

Use a stack to store parent pointer of each node.

Iterative:

```java
public List<Integer> inOrder(Node root) {

    Node cur = root;
    Stack<Integer> stack = new Stack<>();
    List<Integer> res = new LinkedList<>();

    stack.push(root);

    while (!stack.isEmpty()) {
        cur = stack.peek();
        if (cur.left != null) {
            stack.push(cur.left);
        } else {
            res.add(cur.val);
            stack.pop();
            if (cur.right != null) {
                cur = cur.right;
            }
        }
    }
}
```

Iterative without using stack

```java
void inOrder (Node root) {

    Node curr = root;
    while (curr != null) {
        if (curr.left != null) {

            Node pre = curr.left;

            while (pre.right != null && pre.right != curr) {
                pre = pre.right;
            }
            if (pre.right == null) {
                // Threaded property for this node was not set. Set it now
                pre.right = curr;
                curr = curr.left; // Thread created. Switch to this subtree now
            } else {
                // This means pre.right = curr
                // Which implies that thread for this was set already, 
                // So we do not need to traverse this subtree again
                pre.right = null; // reset the thread we created earlier
                print (curr); 
                curr = curr.right;
            }
        } else {
            // no left subtree, print yourself and get to right subtree
            print (curr); 
            // we will never get right = null till the end because of above threads
            curr = curr.right; 
        }
    }
}
```

Recursive:

```java
public List<Integer> inOrder(Node root) {
    List <Integer> res = new LinkedList<>();

    if (root !=null){
            helper(root);
    }
 
    return result;
}
 
public void helper(Node root){
    if (p.left!=null) {
        helper(p.left);    
    }
 
    res.add(p.val);
 
    if (p.right!=null) {
        helper(p.right);
    }
}
```