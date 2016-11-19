# Merge k Sorted Lists

Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

**Solution 1**: Use PriorityQueue `N * log(K)`

```java
public class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        
        if (lists == null || lists.length == 0) {
            return null;
        }
        
        int k = lists.length;
        
        Comparator<ListNode> c = new Comparator<ListNode>() {
            @Override
            public int compare(ListNode node1, ListNode node2) {
                int n1 = node1.val;
                int n2 = node2.val;
                if (n1 > n2) {
                    return 1;
                } else if (n1 == n2) {
                    return 0;
                } else {
                    return -1;
                }
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