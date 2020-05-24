### Algorithm

1. We use 2 Heaps to keep track of median
    - maxHeap contains all SMALL elements
    - minHeap contains all LARGE elements
1. We make sure that 1 of the following conditions is always true:
    - maxHeap.size() == minHeap.size()
    - maxHeap.size() - 1 = minHeap.size()

### Solution

```java
class MedianFinder {
    private Queue<Integer> maxHeap = new PriorityQueue(Collections.reverseOrder());
    private Queue<Integer> minHeap = new PriorityQueue();

    public void addNum(int num) {
        if (maxHeap.size() == minHeap.size()) {
            minHeap.add(num);
            maxHeap.add(minHeap.remove());
        } else if (maxHeap.size() > minHeap.size()) {
            maxHeap.add(num);
            minHeap.add(maxHeap.remove());
        } // maxHeap will never be smaller size than minHeap
    }

    public double findMedian() {
        if (maxHeap.isEmpty()) {
            return 0;
        } else if (maxHeap.size() == minHeap.size()) {
            return (maxHeap.peek() + minHeap.peek()) / 2.0;
        } else {
            return maxHeap.peek();
        }
    }
}
```

### Time Complexity

O(log n) for addNum(). O(1) for findMedian()

### Space Complexity

- O(1) for storage of each number
- O(1) for addNum()
- O(1) for findMedian()
