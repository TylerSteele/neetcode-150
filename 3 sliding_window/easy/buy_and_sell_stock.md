# [Best Time to Buy and Sell Stock](https://neetcode.io/problems/buy-and-sell-crypto)

## 4/27/2025

I do remember the sliding window concept, but I'm struggling to remember what it looks like in practice. In this case, I don't know what the size of the window should be. Let's see if I can remember.

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        max_profit = 0
        for window in range(1, len(prices)):
            for index, price in enumerate(prices):
                if ((index + window) <= (len(prices) - 1) and max_profit < (difference := prices[index + window] - price)):
                    max_profit =  difference

        return max_profit
```

I thought I was being clever by breaking it down into different widnow sizes, but I still ended up with n^2 time complexity. This feels like one those things I just have to memorize the solution for.

Okay, that is a good idea to set the min_buy price. It's tough to think directionally like that when you are looking at a list in your notebook. Looking in at it in the plot, the way he drew it in the video, it does seem more intuitive that the minimum buying price would be trackable in one loop.

Wait a second, is this even a sliding window problem? If anything it should be under two pointers based on the other solution. Or it could be under dynamic programming...

Also, the Two Pointer solution is essentially the same thing as the dynamic programming solution, no?

## 5/1/2025

Okay, I should be able to remember this one. The trick is that the lowest value to the left is always the best time to buy.

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        best_buy_index = 0
        maximum_profit = 0
        for index, price in enumerate(prices):
            if (difference := price - prices[best_buy_index]) > maximum_profit:
                maximum_profit = difference
            if price < prices[best_buy_index]:
                best_buy_index = index
        return maximum_profit
```

This was smooth sailing, except I had another off-by-one error. I thought I was being clever and saving one iteration by doing: `for index, price in enumerate(prices[1:]):`, but this messed up the index value such that it was off by one. I could account for that by just adding one whereever I use index, but that's too confusing for the sake of just saving one iteration.

I googled what "sliding window" means, and it says

> method used to efficiently solve problems involving arrays or lists by maintaining a window of elements of a fixed or variable size and moving it across the entire data structure.

I thought it was applicable for fixed sized windows. Because if it isn't then couldn't you consider all two-pointer problems sliding window problems? It being variable size makes it applicable to this problem, I guess, but at that point 'sliding window' loses its meaning imo.
