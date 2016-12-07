# Min Stack

Design a stack that supports **push**, **pop**, **top**, and retrieving the **minimum element** in constant time.
- push(x) -- Push element x onto stack.
- pop() -- Removes the element on top of the stack.
- top() -- Get the top element.
- getMin() -- Retrieve the minimum element in the stack.

**Ideas**:

```java
MinStack minStack = new MinStack(); 
minStack.push(1);   // Stack: 1/null
minStack.push(2);   // Stack: 2/1/null
minStack.push(3);   // Stack: 3/2/1/null
minStack.pop();     // Stack: 2/1/null
minStack.top();     -> Returns 2
minStack.getMin();  -> Returns 1
```
Always keep track of what node **Top** considers is the min at the moment, and update it accordingly (when `top()` or `push()`).

```java
public class MinStack {

    private Node top;

    public MinStack() {
        top = null;
    }

    public int getMin() {        
        return top.min;
    }

    public int top() {
        return top.val;
    }

    public void pop() {
        top = top.next;
    }

    public void push(int x) {
        if (top == null) {    
           top = new Node(x, x);
        } else {
            int min = Math.min(x, getMin());
            Node n = new Node(x, min, top);
            top = n;
        }
    }
     
    private class Node {
        int val;
        int min;
        Node next;

        private Node(int v, int m, Node n) {
            val = v;
            min = m;
            next = n;
        }

        private Node (int v, int m) {
            this(v, m, null);
        }
    }
}
```
