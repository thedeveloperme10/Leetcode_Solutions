### Solution

```java
class Solution {
    public int maxEnvelopes(int[][] envelopes) {
        if (envelopes == null || envelopes.length == 0 || envelopes[0].length != 2) {
            return 0;
        }
        Arrays.sort(envelopes, (a, b) -> {
            if (a[0] != b[0]) {
                return a[0] - b[0];
            } else {
                return b[1] - a[1];
            }
        });

        // Longest Increasing Subsequence Algorithm
        int[] sortedArray = new int[envelopes.length];
        int size = 0;
        for (int[] envelope : envelopes) {
            int num = envelope[1];
            int start = 0;
            int end = size; // 1 element past end of our sortedArray
            while (start != end) {
                int mid = (start + end) / 2;
                if (sortedArray[mid] < num) {
                    start = mid + 1;
                } else {
                    end = mid;
                }
            }
            sortedArray[start] = num;
            if (start == size) {
                size++;
            }
        }
        return size;
    }
}
```

### Time/Space Complexity

-  Time Complexity: O(n log n) due to sorting
- Space Complexity: O(n) for storing `sortedArray` variable
