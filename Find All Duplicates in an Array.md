### Algorithm

1. Loop through the input array to save the number of times each `int` appears, into a `Map`
1. Loop through the `Map` to see which elements appear twice.

### Solution

```java
class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        Map<Integer, Integer> map = new HashMap();
        List<Integer> list = new ArrayList();
        for (int i = 0; i < nums.length; i++) {
            map.merge(nums[i], 1, Integer::sum);
        }
        for (int key : map.keySet()) {
            if (map.get(key) == 2) {
                list.add(key);
            }
        }
        return list;
    }
}
```

### Time/Space Complexity

-  Time Complexity: O(n)
- Space Complexity: O(n)
