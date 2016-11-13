# Merge Two Sorted Lists

Merge two sorted linked lists and return it as a new list. 

The new list should be made by splicing together the nodes of the first two lists.

**Ideas**:

Merge Select

```java
public Node mergeTwoLists(Node n1, Node n2) {
    
    Node res = new Node(0);
    Node n = res;
    
    while (n1 != null && n2 != null) {
        if (n1.val < n2.val) {
            n.next = n1;
            n1 = n1.next;
        } else {
            n.next = n2;
            n2 = n2.next;
        }
        n = n.next;
    }
    
    if (n1 == null) {
        n.next = n2;
    }

    if (n2 == null) {
        n.next = n1;
    }
    
    return res.next;
}
```