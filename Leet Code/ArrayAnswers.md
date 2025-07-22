

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


## 2. 🔗 **Best Time to Buy and Sell Stock**

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock)

---

### ✅ **Problem Summary**

You're given an array `prices[]` where `prices[i]` is the price of a stock on the `i`-th day.
You can buy and sell **once** — find the **maximum profit** you can achieve.

---

### 💡 **Java Code 

```java
public class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;  
        int maxProfit = 0;                 

        for (int price : prices) {
            if (price < minPrice) {
                minPrice = price;  
            } else if (price - minPrice > maxProfit) {
                maxProfit = price - minPrice; 
            }
        }

        return maxProfit;
    }
}
```

---


## 3. 🔗 **Remove Duplicates from Sorted Array**

[https://leetcode.com/problems/remove-duplicates-from-sorted-array](https://leetcode.com/problems/remove-duplicates-from-sorted-array)

---

### ✅ **Problem Summary**

Given a **sorted** array `nums`, remove the duplicates **in-place** such that each element appears only **once**.
Return the new length of the array after duplicates are removed.

⚠️ Do **not** use extra space for another array.

---

### 💡 **Java Code (Two Pointers - O(n))**

```java
public class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) return 0;

        int i = 0;  // slow pointer

        for (int j = 1; j < nums.length; j++) {
            if (nums[j] != nums[i]) {
                i++;                
                nums[i] = nums[j]; 
            }
        }

        return i + 1; 
    }
}
```

---

