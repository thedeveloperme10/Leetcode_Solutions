# Solution 1 - Binary Search

Use [binary search](https://github.com/RodneyShag/LeetCode_solutions/blob/master/Solutions/Binary%20Search.md) to keep guessing different `int` values that may qualify as the square root of `n`

### Code

```java
class Solution {
    public boolean isPerfectSquare(int n) {
        if (n < 0) {
            return false;
        }
        int lo = 0;
        int hi = n;
        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            long squared = (long) mid * mid; // use `long` to avoid integer overflow
            if (squared == n) {
                return true;
            } else if (squared < n) {
                lo = mid + 1;
            } else {
                hi = mid - 1;
            }
        }
        return false;
    }
}
```

### Time/Space Complexity

-  Time Complexity: O(log n)
- Space Complexity: O(1)
