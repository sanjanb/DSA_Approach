### **Brute Force Approach for Maximum Product Subarray**

#### **Approach**  
The brute force approach checks every possible subarray and calculates its product. We keep track of the maximum product found.

---

### **Code Implementation**
```python
class Solution(object):
    def maxProduct(self, nums):
        n = len(nums)
        max_product = float('-inf')  # Initialize with the smallest possible value

        # Iterate through all possible subarrays
        for i in range(n):
            product = 1
            for j in range(i, n):
                product *= nums[j]  # Calculate product of subarray nums[i:j+1]
                max_product = max(max_product, product)  # Update max product
        
        return max_product
```

---

### **Step-by-Step Breakdown**
1. **Initialize** `max_product` to the smallest possible value.
2. **Iterate** over all starting indices `i`.
3. **Iterate** over all ending indices `j` (starting from `i`).
4. Compute the **product** of the subarray `nums[i:j+1]` in the inner loop.
5. **Update** `max_product` if a larger product is found.
6. Return `max_product`.

---

### **Example Walkthrough**
#### **Input:**
```python
nums = [2, 3, -2, 4]
```
#### **Execution:**
| `i` | `j` | Subarray        | Product | `max_product` |
|-----|-----|----------------|---------|--------------|
| 0   | 0   | `[2]`          | 2       | 2            |
| 0   | 1   | `[2,3]`        | 6       | 6            |
| 0   | 2   | `[2,3,-2]`     | -12     | 6            |
| 0   | 3   | `[2,3,-2,4]`   | -48     | 6            |
| 1   | 1   | `[3]`          | 3       | 6            |
| 1   | 2   | `[3,-2]`       | -6      | 6            |
| 1   | 3   | `[3,-2,4]`     | -24     | 6            |
| 2   | 2   | `[-2]`         | -2      | 6            |
| 2   | 3   | `[-2,4]`       | -8      | 6            |
| 3   | 3   | `[4]`          | 4       | 6            |

#### **Output:**
```python
6
```
(Since `[2,3]` gives the maximum product)

---

### **Time & Space Complexity**
- **Time Complexity**: 🕒 **O(N²)** → We iterate through all subarrays.
- **Space Complexity**: 💾 **O(1)** → No extra space used.
