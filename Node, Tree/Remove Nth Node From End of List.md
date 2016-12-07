# Remove Nth Node From End of List

Given a linked list, remove the nth node from the end of list and return its head.

**Ideas**:

- Given linked list: `1->2->3->4->5`, and `n = 2`.

- After removing the second node from the end, the linked list becomes `1->2->3->5`.

- Advance the R pointer by n steps, and then move L and R at the same pace till the end of list.

```java
public Node removeNthFromEnd(Node head, int n) {
    
    Node res = new Node(0);
    res.next = head;

    Node l = res;
    Node r = res;
    
    while (r.next != null) {
        if (n > 0) {
            r = r.next;
            n--;
        } else {
            r = r.next;
            l = l.next;
        }
    }
    
    l.next = l.next.next;

    return res.next;
}

```