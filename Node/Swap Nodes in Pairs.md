# Swap Nodes in Pairs

Given a linked list, swap every two adjacent nodes and return its head.

**Ideas**:

- Given `1->2->3->4`  ->  `2->1->4->3`.

- Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.

```java
public Node swapPairs(Node head) {
    Node res = new Node(0);
    Node n = res;
    n.next = head;
    
    while(n.next != null && n.next.next != null) {
        Node first = n.next;
        Node second = n.next.next;
        first.next = second.next;
        second.next = first;
        n.next = second;
        n = first;
    }
    
    return res.next;
}


```