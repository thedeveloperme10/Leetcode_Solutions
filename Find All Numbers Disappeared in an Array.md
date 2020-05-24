### Algorithm

1. Create a Set of elements with values 1 to n (inclusive)
1. Loop through input array to remove corresponding elements from our Set.

### Solution

```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        Set<Integer> set = new HashSet();
        for (int i = 1; i <= nums.length; i++) {
            set.add(i);
        }
        for (int num : nums) {
            set.remove(num);
        }
        return new ArrayList(set);
    }
}
```

### Time/Space Complexity

-  Time Complexity: O(n)
- Space Complexity: O(n)
