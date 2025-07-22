

## 1. 🔗 **Two Sum**
[https://leetcode.com/problems/two-sum](https://leetcode.com/problems/two-sum)

---

### ✅ **Problem Summary**

Given an array of integers `nums` and an integer `target`, return **indices** of the two numbers such that they add up to `target`.

---

### 💡 **Java Code Using HashMap 

```java
import java.util.HashMap;

public class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();  

        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];

            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }

            map.put(nums[i], i);
        }

        
        return new int[] {}; 
    }
}
```

---

