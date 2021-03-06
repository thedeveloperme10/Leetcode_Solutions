### Algorithm

1. Create a new `int result`.
1. Loop through the bits of the input `int n` and update `result` with the appropriate bits

### Solution

```java
public class Solution {
    public int reverseBits(int n) {
        int result = 0;
        for (int i = 0; i < 32; i++) { // 32 bits in Java int
            if (getBit(n, i)) {
                result = setBit(result, 31 - i);
            }
        }
        return result;
    }

    private boolean getBit(int n, int bit) {
        return (n & (1 << bit)) != 0;
    }

    private int setBit(int n, int bit) {
        return n | (1 << bit);
    }
}
```

### Time/Space Complexity

-  Time Complexity: O(1)
- Space Complexity: O(1)
