

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


## 4. 🔗 **Move Zeroes**

[https://leetcode.com/problems/move-zeroes](https://leetcode.com/problems/move-zeroes)

---

### ✅ **Problem Summary**

Given an integer array `nums`, move all the `0`s to the **end** while maintaining the **relative order** of the non-zero elements.

Do it **in-place** (no extra array), and in **O(n)** time.

---

### 💡 **Java Code (Two Pointers)**

```java
public class Solution {
    public void moveZeroes(int[] nums) {
        int index = 0;  // points to the place to insert non-zero

        
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[index] = nums[i];
                index++;
            }
        }

       
        while (index < nums.length) {
            nums[index] = 0;
            index++;
        }
    }
}
```

---


## 5.🔗 **Maximum Subarray**

[https://leetcode.com/problems/maximum-subarray](https://leetcode.com/problems/maximum-subarray)

---

### ✅ **Problem Summary**

Given an integer array `nums`, find the **contiguous subarray (at least one number)** that has the **largest sum**, and return that sum.

---

### 💡 **Java Code Using Kadane’s Algorithm (O(n))**

```java
public class Solution {
    public int maxSubArray(int[] nums) {
        int maxSoFar = nums[0];   
        int currentSum = nums[0]; 

        for (int i = 1; i < nums.length; i++) {
            
            currentSum = Math.max(nums[i], currentSum + nums[i]);
            maxSoFar = Math.max(maxSoFar, currentSum);
        }

        return maxSoFar;
    }
}
```

---


## 6. 🔗 **Contains Duplicate**

[https://leetcode.com/problems/contains-duplicate](https://leetcode.com/problems/contains-duplicate)

---

### ✅ **Problem Summary**

Given an integer array `nums`, return `true` if **any value appears at least twice** in the array, and `false` if every element is distinct.

---

### 💡 **Java Code Using HashSet (O(n) time, O(n) space)**

```java
import java.util.HashSet;

public class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<>();

        for (int num : nums) {
            if (set.contains(num)) {
                return true;  
            }
            set.add(num);  
        }

        return false;  
    }
}
```

---




