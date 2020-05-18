### Solution

```java
class Solution {
    public String addBinary(String s1, String s2) {
        if (s1 == null) {
            return s2;
        } else if (s2 == null) {
            return s1;
        }

        int carry = 0;
        int i = s1.length() - 1;
        int j = s2.length() - 1;
        StringBuffer sb = new StringBuffer();

        while (i >= 0 || j >= 0 || carry != 0) {
            int sum = carry;
            if (i >= 0 && s1.charAt(i) == '1') {
                sum++;
            }
            if (j >= 0 && s2.charAt(j) == '1') {
                sum++;
            }
            int digit = sum % 2;
            carry = sum / 2;
            sb.append(digit);
            i--;
            j--;
        }

        return sb.reverse().toString();
    }
}
```

### Time/Space Complexity

-  Time Complexity: O(n + m)
- Space Complexity: O(n + m)
