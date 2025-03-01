### **Explanation of the Code**
This function calculates the Hamming weight (the number of 1's) in the binary representation of an integer `n` using a simple loop with modulo and bit shifting.

---

### **Step-by-Step Breakdown**
```python
class Solution(object):
    def hammingWeight(self, n):
        ans = 0                    # Initialize a counter for the number of 1 bits.
        
        while n != 0:              # Continue looping until n becomes 0.
            ans += n % 2           # n % 2 gives the remainder when dividing by 2, which is 1 if the least significant bit is 1.
            n = n >> 1             # Right shift n by 1 to move to the next bit.
            
        return ans                 # Return the total count of 1's.
```

1. **Initialization:**  
   - `ans = 0` initializes a counter to store the number of 1's encountered.
   
2. **Loop Over Each Bit:**  
   - The `while n != 0` loop iterates as long as there are bits left in `n`.  
   - `n % 2` extracts the least significant bit: it adds 1 to `ans` if that bit is 1, or 0 if it's 0.
   - `n = n >> 1` shifts the bits of `n` one position to the right, discarding the bit just processed.
   
3. **Termination:**  
   - When `n` becomes 0, all bits have been processed, and the function returns `ans`, the count of 1's.

---

### **How It Works**
- **Bit Extraction:**  
  Each iteration extracts the rightmost bit using `n % 2` and adds it to the counter.
  
- **Bit Shifting:**  
  The right shift (`n >> 1`) effectively divides `n` by 2 and moves the next bit into position for evaluation.
  
- **Complete Coverage:**  
  The loop continues until all bits in `n` are examined.

---

### **Example Walkthrough**
Suppose `n = 11`, whose binary representation is `1011`:

| Step | Value of `n` (binary) | `n % 2` (bit) | `ans` (cumulative) | Action               |
|------|-----------------------|---------------|--------------------|----------------------|
| 1    | `1011` (11)           | 1             | 0 + 1 = 1          | Add 1 to `ans`       |
| 2    | `101` (5)             | 1             | 1 + 1 = 2          | Add 1 to `ans`       |
| 3    | `10` (2)              | 0             | 2 + 0 = 2          | Add 0 to `ans`       |
| 4    | `1` (1)               | 1             | 2 + 1 = 3          | Add 1 to `ans`       |
| 5    | `0`                   | -             | Loop ends          |                      |

**Output:**  
The function returns `3` since there are three 1's in the binary representation of 11.

---

### **Time & Space Complexity**
- **Time Complexity:**  
  O(k) where k is the number of bits in the integer. For a 32-bit integer, this is O(32) which is constant time.
  
- **Space Complexity:**  
  O(1) since only a few extra variables are used regardless of the input size.

---

### **Analysis Note**
After reviewing several educational resources and articles on bit manipulation and Hamming weight calculations (e.g., from GeeksforGeeks and LeetCode discussions), the above explanation and code structure are confirmed to be a standard approach for this problem.

Would you like further details on alternative approaches (like using bit manipulation tricks such as `n &= n - 1`)? 🚀
