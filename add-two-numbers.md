# Add Two Number

Given two linked lists (represent non-negative numbers). 

The digits are stored in **reverse order**.

Add them and return a new linked list.

**Example**

Given (**2** -> 4 -> 3) + (**5** -> 6 -> 4)

Return (**7** -> 0 -> 8)

**Ideas:** 

Reverse order: Number 123 -> Linked List (3 -> 2 -> 1), because: 
- When adding numbers, reading from right to left, 
- But in linked list, reading from left to right.

```java
public Node addTwoNumbers(Node A, Node B) {
    
    // Set up res points to Node 0, to bypass checking on A or B
    // We can always return res.next as a result
    Node res = new Node(0);
    Node p = res;
    int carry = 0;
    
    // Check carry == 1 because in such case [5] + [5] -> [1,0]
    while (A != null || B != null || carry == 1) {
        
        if (A != null) {
            carry += A.val;
            A = A.next;
        }
            
        if (B != null) {
            carry += B.val;
            B = B.next;
        }
        
        int val = carry % 10;
        carry = carry / 10;
        
        Node n = new Node(val);
        // Link the bridge between p and n
        p.next = n;
        // Advance p, don't have to worry about loosing the path 
        // because we already have res to keep track of the HEAD
        p = p.next;
    }

    return res.next;
}
```




