# Best Time to Buy and Sell Stock Guide

This guide provides a detailed explanation and implementation of the solution to the "Best Time to Buy and Sell Stock" problem. The goal is to determine the maximum profit that can be achieved by buying and selling a stock, given an array of stock prices where each index represents a different day.

---

## Purpose of the Code

The goal is to find the maximum profit that can be made by buying and selling a stock, given an array of stock prices where each index represents a different day.

---

## Algorithm: Two-Pointer Approach

- **`l` (left pointer):** Represents the buying day.
- **`r` (right pointer):** Represents the selling day.

This approach efficiently tracks the lowest buying price and the maximum potential profit in a single iteration through the prices array.

---

## Detailed Walkthrough

```python
def maxProfit(prices):
    # Initialize left and right pointers
    l, r = 0, 1
    # Track maximum profit
    maxp = 0

    # Iterate through the prices
    while r < len(prices):
        # If buying price is less than selling price
        if prices[l] < prices[r]:
            # Calculate current profit
            profit = prices[r] - prices[l]
            # Update maximum profit if current profit is higher
            maxp = max(maxp, profit)
        else:
            # If current price is lower, update buying point
            l = r

        # Move to next day
        r += 1

    return maxp
```

---

## Key Steps

1. **Initialize Pointers:** Start with the first day as the buying day (index 0).
2. **Compare Prices:** Compare the buying price with subsequent selling prices.
3. **Calculate Profit:** If the selling price is higher, calculate the potential profit.
4. **Update Maximum Profit:** Update the maximum profit if the current profit is higher.
5. **Reset Buying Day:** If the selling price is lower, reset the buying day to the current day.
6. **Iterate:** Continue until all prices are checked.

---

## Example

```python
prices = [7, 1, 5, 3, 6, 4]
# Best buy day: day with price 1
# Best sell day: day with price 6
# Maximum profit: 6 - 1 = 5
```

---

## Complexity Analysis

### Time Complexity: O(n)
- The algorithm makes a single pass through the prices array.
- Each element is visited once.

### Space Complexity: O(1)
- Only two pointers (`l` and `r`) and a variable (`maxp`) are used.
- No extra data structures are required.

---

## Conclusion

The two-pointer approach elegantly solves the "Best Time to Buy and Sell Stock" problem by dynamically tracking the lowest buying price and the maximum potential profit in a single iteration. This method is efficient and easy to understand, making it an excellent choice for solving this problem.

---

**Happy Coding!** 🚀
