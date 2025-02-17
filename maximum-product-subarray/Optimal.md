### **Optimal Approach for Maximum Product Subarray**  
We use **Kadane’s Algorithm for Products**, handling **negative numbers** carefully. Instead of tracking just one max product, we maintain both **max_so_far** and **min_so_far** because a negative number can turn a small product into a large one.

---

### **Code Implementation**
```python
class Solution(object):
    def maxProduct(self, nums):
        if not nums:
            return 0
        
        max_so_far = nums[0]
        min_so_far = nums[0]
        result = nums[0]

        for i in range(1, len(nums)):
            if nums[i] < 0:
                max_so_far, min_so_far = min_so_far, max_so_far  # Swap
            
            max_so_far = max(nums[i], nums[i] * max_so_far)
            min_so_far = min(nums[i], nums[i] * min_so_far)

            result = max(result, max_so_far)
        
        return result
```

---

### **Step-by-Step Breakdown**
1. **Initialize variables**:
   - `max_so_far`: Tracks the largest product subarray.
   - `min_so_far`: Tracks the smallest (important for negatives).
   - `result`: Stores the final max product.
   
2. **Iterate through `nums`**:
   - **Swap `max_so_far` and `min_so_far`** if `nums[i]` is negative (because multiplying by a negative flips the values).
   - **Update `max_so_far`**: Choose between `nums[i]`, `nums[i] * max_so_far`, or `nums[i] * min_so_far`.
   - **Update `min_so_far`** similarly.
   - **Update `result`** with the highest `max_so_far`.

---

### **Example Walkthrough**
#### **Input:**
```python
nums = [2, 3, -2, 4]
```
#### **Execution:**
| `i` | `nums[i]` | `max_so_far` | `min_so_far` | `result` |
|----|----|------------|------------|--------|
| 0  | 2  | 2          | 2          | 2      |
| 1  | 3  | 6          | 3          | 6      |
| 2  | -2 | -2 ↔ 6 → -12 | 6 ↔ -2 → -6 | 6      |
| 3  | 4  | 4          | -24         | 6      |

#### **Output:**
```python
6
```
(Max product subarray is `[2,3]`)

---

### **Time & Space Complexity**
- **Time Complexity**: 🕒 **O(N)** → Single pass through the array.
- **Space Complexity**: 💾 **O(1)** → Constant extra space.

**Optimized for performance! 
