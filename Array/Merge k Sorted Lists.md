# Merge k Sorted Lists

Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

**Solution 1**: Use PriorityQueue `N * log(K)`

```java
public class Solution {
    public Node mergeKLists(Node[] lists) {
        
        if (lists == null || lists.length == 0) {
            return null;
        }
        
        int k = lists.length;
        
        Comparator<Node> c = new Comparator<Node>() {
            // +1, 0 or -1
            @Override
            public int compare(Node node1, Node node2) {
                return node1.val - node.val;
            }
        };
        
        PriorityQueue<ListNode> q = new PriorityQueue<ListNode>(k, c);
        
        ListNode res = new ListNode(0);
        ListNode tail = res;
        
        //  Put all the head of each list into the queue
        for (ListNode node: lists) {
            // Check of case such as [[]]
            if (node != null) {
                q.add(node);
            }
        }
            
        // Get the smallest in the queue, and add to result            
        while (!q.isEmpty()){

            ListNode smallest = q.poll();
            tail.next = smallest;
            tail = tail.next;
            
            if (tail.next != null) {
                q.add(tail.next);
            }
        }
        
        return res.next;
    }
}
```

Solution 2: Merge Sort

```java
public ListNode mergeKLists(ListNode[] lists) {
    
    if (lists.length == 0) {
        return null;
    }
    
    int l = 0;
    int r = lists.length - 1;
    
    while (l < r) {

        // Use left and right pointers to merge
        while (l < r) {
            lists[l] = merge2Lists(lists[l], lists[r]);
            l++;
            r--;
        }

        // The range now reduced by half
        // Repeat until everything merged with lists[0]
        l = 0;
    }
    
    return lists[0];
}

public Node merge2Lists(Node A, Node B) {
    
    Node res = new Node(0);
    Node tail = res;
    
    while (A != null && B != null) {
        
        int a = A.val;
        int b = B.val;
        
        if (a > b) {
            tail.next = B;
            B = B.next;
        } else {
            tail.next = A;
            A = A.next;
        }
        
        tail = tail.next;
    }
    
    if (A != null) {
        tail.next = A;
    }

    if (B != null) {
        tail.next = B;
    }
    
    return res.next;
    }
}
```