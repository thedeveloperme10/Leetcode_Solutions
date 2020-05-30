### Algorithm
1. Calculate and store length of SCS in `int[][]` for each i, j
1. Reconstruct the actual String representing SCS

### Solution

```java
class Solution {
    public String shortestCommonSupersequence(String X, String Y) {
        // find length of Shortest Common SuperSequence (SCS) for each i, j
        int m = X.length();
        int n = Y.length();
        int[][] scs = new int[m + 1][n + 1];
        for (int i = 0; i <= m; i++) {
            for (int j = 0; j <= n; j++) {
                if (i == 0) {
                    scs[i][j] = j;
                } else if (j == 0) {
                    scs[i][j] = i;
                } else if (X.charAt(i - 1) == Y.charAt(j - 1)) { // X, Y are 1-indexed in our definition, 0-indexed in code
                    scs[i][j] = 1 + scs[i - 1][j - 1];
                } else {
                    scs[i][j] = 1 + Math.min(scs[i - 1][j], scs[i][j - 1]);
                }
            }
        }

        // reconstruct the actual String representing SCS
        StringBuffer sb = new StringBuffer();
        int i = m;
        int j = n;

        while (i > 0 && j > 0) {
            if (X.charAt(i - 1) == Y.charAt(j - 1)) {
                sb.insert(0, X.charAt(i - 1));
                i--;
                j--;
            }
            // Tricky. The smaller scs determines which character to insert.
            else if (scs[i - 1][j] < scs[i][j - 1]) {
                sb.insert(0, X.charAt(i - 1));
                i--;
            } else {
                sb.insert(0, Y.charAt(j - 1));
                j--;
            }
        }

        // Only 1 of these will run
        while (i > 0) {
            sb.insert(0, X.charAt(i - 1));
            i--;
        }
        while (j > 0) {
            sb.insert(0, Y.charAt(j - 1));
            j--;
        }

        return sb.toString();
    }
}
```

### Time/Space Complexity

-  Time Complexity: O(m * n) due to our nested for loops
- Space Complexity: O(m * n) due to our 2-D array
