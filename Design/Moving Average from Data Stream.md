# Moving Average from Data Stream

Given a stream of integers and a window size, calculate the moving average of all integers in the sliding window.

For example:
```
MovingAverage m = new MovingAverage(3);
m.next(1) = 1
m.next(10) = (1 + 10) / 2
m.next(3) = (1 + 10 + 3) / 3
m.next(5) = (10 + 3 + 5) / 3
```
| LinkeList          | ArrayDeque             |
|--------------------|------------------------|
| new LinkedList<>() | new ArrayDeque<>(size) |
| .add(val)          | .offer(val)            |
| .remove()          | .poll()                |



```java
public class MovingAverage {
    
    private Queue<Integer> q;
    private double sum = 0.0;
    private final int size;
    
    public MovingAverage(int s) {
        q = new LinkedList<Integer>();
        size = s;
    }
    
    public double next(int val) {
        if (q.size() == size) {
            sum -= q.remove();
        }

        q.add(val);
        sum += val;

        return (double) (sum) / q.size();
    }
}
```


