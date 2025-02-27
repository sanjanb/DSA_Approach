# Finding Minimum in Rotated Sorted Array Guide

This guide provides a detailed explanation and implementation of the solution to find the minimum element in a rotated sorted array. The goal is to determine the smallest element in an array that has been rotated at some pivot unknown to you beforehand.

---

## Table of Contents

- [Purpose of the Code](#purpose-of-the-code)
- [Algorithm: Binary Search Approach](#algorithm-binary-search-approach)
- [Detailed Walkthrough](#detailed-walkthrough)
- [Key Steps](#key-steps)
- [Example](#example)
- [Complexity Analysis](#complexity-analysis)
- [Optimality of the Solution](#optimality-of-the-solution)
- [Conclusion](#conclusion)

---

## Purpose of the Code

The goal is to find the minimum element in a rotated sorted array. A rotated sorted array is a sorted array that has been rotated at some unknown pivot, meaning it is divided into two sorted subarrays.

---

## Algorithm: Binary Search Approach

- **`low` and `high`:** Pointers representing the current search bounds within the array.
- **`mid`:** The middle index between `low` and `high`.
- **`ans`:** Tracks the minimum value found during the search.

This approach uses binary search to efficiently find the minimum element by leveraging the properties of the rotated sorted array.

---

## Detailed Walkthrough

```python
import sys

class Solution(object):
    def findMin(self, nums):
        # Initialize low and high pointers
        low = 0
        high = len(nums) - 1
        # Initialize ans to a large value
        ans = sys.maxsize

        # Binary search loop
        while low <= high:
            # Calculate the middle index
            mid = (low + high) // 2

            # If the array is sorted, the minimum is at the low index
            if nums[low] <= nums[high]:
                ans = min(ans, nums[low])
                break

            # If the left part is sorted, the minimum is not in this part
            if nums[low] <= nums[mid]:
                ans = min(ans, nums[low])
                low = mid + 1
            else:
                # The minimum is in the right part
                ans = min(ans, nums[mid])
                high = mid - 1

        # Return the minimum value found
        return ans
```

---

## Key Steps

1. **Initialize Pointers:** Start with `low` at the beginning and `high` at the end of the array.
2. **Binary Search Loop:** Use a loop to perform binary search until `low` exceeds `high`.
3. **Calculate Mid:** Determine the middle index `mid` between `low` and `high`.
4. **Check Sorted Condition:** If the subarray from `low` to `high` is sorted, the minimum is at `low`.
5. **Adjust Search Bounds:**
   - If the left part (from `low` to `mid`) is sorted, the minimum is not in this part, so move `low` to `mid + 1`.
   - Otherwise, the minimum is in the right part, so move `high` to `mid - 1`.
6. **Update Minimum:** Track the minimum value found during the search.
7. **Return Result:** After the loop, return the minimum value found.

---

## Example

```python
nums = [4, 5, 6, 7, 0, 1, 2]
# The array is rotated, and the minimum element is 0.
```

---

## Complexity Analysis

### Time Complexity: O(log n)
- The algorithm uses binary search, reducing the search space by half in each iteration.

### Space Complexity: O(1)
- Only a few variables are used, and no extra data structures are required.

---

## Optimality of the Solution

The binary search approach is optimal for this problem due to the following reasons:

- **Efficiency:** The algorithm achieves a time complexity of O(log n), which is the best possible time complexity for searching in a sorted or partially sorted array.
- **Space Usage:** The space complexity is O(1), indicating that the algorithm uses a constant amount of extra space regardless of the input size.
- **Comparison Count:** The algorithm minimizes the number of comparisons needed to find the minimum element, making it efficient even for large arrays.

Given these factors, the binary search approach is considered optimal for finding the minimum element in a rotated sorted array.

---

## Conclusion

The binary search approach efficiently finds the minimum element in a rotated sorted array by leveraging the properties of the array's rotation. This method is optimal for solving this problem due to its logarithmic time complexity and constant space usage.

---

**Happy Coding!** 🚀
