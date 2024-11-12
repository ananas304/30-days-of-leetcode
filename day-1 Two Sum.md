# 1. Two Sum  `Easy`
link: https://leetcode.com/problems/two-sum/
## Hint:
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

#### Example 1:
**Input**: `nums = [2,7,11,15]`, `target = 9`  
**Output**: `[0,1]`  
**Explanation**: Because `nums[0] + nums[1] == 9`, we return `[0, 1]`.

#### Example 2:
**Input**: `nums = [3,2,4]`, `target = 6`  
**Output**: `[1,2]`

#### Example 3:
**Input**: `nums = [3,3]`, `target = 6`  
**Output**: `[0,1]`

---

## Solution:
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        prevmap = {}
        for i, n in enumerate(nums):
            diff = target - n
            if diff in prevmap:
                return [prevmap[diff], i]
            prevmap[n] = i
        return
```
---

### Explaination 
1. Brute force:
   lets take an array `| 2 | 1 | 5 | 3 |` and `target = 4` then we can check each number with it's consecutive number and check if the sum = target.
   for example `2 + 1 = 3 != 4`, `2 + 5 = 7 != 4`, `2 + 3 = 5 != 4`, `1 + 5 = 6 != 4`, `1 + 3 = 4`. the time complexity is O(n^2)

2. Optimal solution:
   We use a `hashmap`. We are looking for `4 - 1 = 3`. we just need to make sure value 3 exists in the array. We map each value to the index of each value.
   | 0 | 1 | 2 | 3 | is the index of below array
   | 2 | 1 | 5 | 3 | is the array. We subtract each value with `target` and the check if the `value` exists in the `mashmap` if it does not then add that value to the hashmap along with the index value. 
   
   - `4 - 2 = 2`, 2 does not exist in the hashmap so we add 2 it to the hashmap.
   - `4 - 1 = 3`, 3 does not exist in the hashmap so we add 1 it to the hashmap.
   - `4 - 5 = -1`, -1 does not exist in the hashmap so we add 5 it to the hashmap.
   - `4 - 3 = 1`, 1 does exist in the hashmap. so return their indexes as [1, 3]
  
   mashmap: 
   | Index | Value |
   |-------|-------|
   |   0   |   2   |
   |   1   |   1   | <---
   |   2   |   5   |

 #### Why does it work: 
 - Let's say we an array, and we are aware that the sum of two elements will gaurentee the target. We iterate through the array and find the first element, in the above example it was '1' (which is now present in the hashmap), and then we iterate through the array and find the second element. 
- *The elements after the second element will not be present in the hashmap*, as we found our two elements whose sum gives us the target value and *we itterate through the array only once.* Hence the **time complexity** is `O(n)` and the **space complexity** is `O(n)`


link: https://youtu.be/KLlXCFG5TnA?si=IS2eXAR_ITymOdTL
