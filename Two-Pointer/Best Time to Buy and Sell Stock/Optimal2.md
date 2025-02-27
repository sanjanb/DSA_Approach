# Best Time to Buy and Sell Stock Guide

This guide provides a detailed explanation and implementation of the solution to the "Best Time to Buy and Sell Stock" problem. The goal is to determine the maximum profit that can be achieved by buying and selling a stock, given an array of stock prices where each index represents a different day.

---

## Purpose of the Code

The goal is to find the maximum profit that can be made by buying and selling a stock, given an array of stock prices where each index represents a different day.

---

## Algorithm: Single Pass Approach

- **`buy`:** Represents the lowest price encountered so far, which is the optimal day to buy.
- **`profit`:** Tracks the maximum profit observed during the iteration.

This approach efficiently tracks the lowest buying price and the maximum potential profit in a single iteration through the prices array.

---

## Detailed Walkthrough

```python
class Solution(object):
    def maxProfit(self, prices):
        # Initialize the buying price to the first day's price
        buy = prices[0]
        # Initialize maximum profit to 0
        profit = 0

        # Iterate through the prices starting from the second day
        for i in range(1, len(prices)):
            # If current price is lower than the buying price, update buying price
            if prices[i] < buy:
                buy = prices[i]
            # If current profit is higher than the maximum profit, update maximum profit
            elif prices[i] - buy > profit:
                profit = prices[i] - buy

        # Return the maximum profit
        return profit
```

---

## Key Steps

1. **Initialize Variables:** Start with the first day's price as the buying price and set the maximum profit to 0.
2. **Iterate Through Prices:** Loop through the prices starting from the second day.
3. **Update Buying Price:** If the current price is lower than the buying price, update the buying price.
4. **Calculate Profit:** If the current profit (difference between the current price and the buying price) is higher than the maximum profit, update the maximum profit.
5. **Return Result:** After the loop, return the maximum profit.

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
- Only two variables (`buy` and `profit`) are used.
- No extra data structures are required.

---

## Conclusion

The single pass approach elegantly solves the "Best Time to Buy and Sell Stock" problem by dynamically tracking the lowest buying price and the maximum potential profit in a single iteration. This method is efficient and easy to understand, making it an excellent choice for solving this problem.

---

**Happy Coding!** 🚀
