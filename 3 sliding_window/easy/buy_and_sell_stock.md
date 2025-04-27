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
