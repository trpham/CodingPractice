# Two Sum III - Data structure design

Design and implement a **TwoSum** class. It should support the following operations: **add** and **find**.

- add - Add the number to an internal data structure.

- find - Find if there exists any pair of numbers which sum is equal to the value.


- Duplicates allowed such as: `add(2), add(2), find(4)`

For example:
```
add(1); 
add(3); 
add(5);
find(4) -> true
find(7) -> false
```

```java
public class TwoSum {
    
    // Map a number to its count (duplicates)
    private Map <Integer, Integer> map = new HashMap<>();

    // List of all unique numbers added
    private List <Integer> list = new ArrayList<>();
    
    public void add(int num) {
        if (!map.containsKey(num)) {
            map.put(num, 1);
            list.add(num);
        } else {
            map.put(num, map.get(num) + 1);
        }
    }
    
    public boolean find(int val) {
        for (int i = 0; i < list.size(); i++) {
            int num = list.get(i);
            int dif = val - num;

            // No duplicate as: (1, 2), find(3)
            if (num != dif && map.containsKey(dif)) {
                return true;
            }
            
            // With duplicates as: (2, 2), fine(4)
            if (num == dif && map.get(num) > 1) {
                return true;
            }
        }

        return false;
    }
}
```