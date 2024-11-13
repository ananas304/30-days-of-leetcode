# 121. Best Time to Buy and Sell Stock `Easy`
link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

- You are given an array `prices` where `prices[i]` is the price of a given stock on the `i`th day.
- You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.
- Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return `0`.

## Examples

### Example 1:
**Input**: `prices = [7,1,5,3,6,4]`  
**Output**: `5`  
**Explanation**: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = `6 - 1 = 5`.  
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

### Example 2:
**Input**: `prices = [7,6,4,3,1]`  
**Output**: `0`  
**Explanation**: In this case, no transactions are done and the max profit = `0`.

## Constraints:
- `1 <= prices.length <= 10^5`
- `0 <= prices[i] <= 10^4`
  
---

## Solution:
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        l, r = 0 ,1                    #left = buy, right = sell
        maxP = 0

        while r < len(prices):
            if prices[l] < prices[r]:
                profit = prices[r] - prices[l]
                maxP = max(maxP, profit)
            else:
                l = r
            r += 1

        return maxP      
```

### Explanation:
- We have prices = [7,1,5,3,6,4], we need to maximize the profit by `buying low` and `selling high`. If we were to buy on `day 2` where the `price = 1` and sell on `day 5` where the `price = 6`, the `profit = 6 - 1 = 5`.
- We can use two pointers where pointer `L = buy` and pointer `R = sell`.
  
1.  | 7 | 1 | 5 | 3 | 6 | 4 |  
2.  | L | R | _ | _ | _ | _ |        here, the buy is more than sell, so we move the pointers forward.
3.  | _ | L | R | _ | _ | _ |        here, the buy is less than sell, `max_profit = 5 - 1 = 4` which is the max profit so far, we keep the `L` pointer on 1 as it is the lowest soo far.
4.  | _ | L | _ | R | _ | _ |        here, the buy is less than sell, but the profit would be `3 - 1 = 2 < max_profit` so we move the `R` pointer.
5.  | _ | L | _ | _ | R | _ |        here, the buy is less than sell, but the profit would be `6 - 1 = 5 > max_profit` so the max_profit is updated and we move the `R` pointer.
6.  | _ | L | _ | _ | _ | R |        here, the buy is less than sell, but the profit would be `4 - 1 = 3 < max_profit` so we move the `R` pointer.

</br>

-  Time complexity = O(n), Space complexity = O(1)
   
link: https://youtu.be/1pkOgXD63yU?si=sdOAz0t_M64V2m8X
 
