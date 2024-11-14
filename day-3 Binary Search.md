# 704. Binary Search `Easy`
link: https://leetcode.com/problems/binary-search

**Given**: An array of integers `nums` which is sorted in ascending order, and an integer `target`.  
**Goal**: Write a function to search `target` in `nums`. If `target` exists, return its index. Otherwise, return `-1`.

**Note**: You must write an algorithm with `O(log n)` runtime complexity.

## Examples

### Example 1:
**Input**: `nums = [-1,0,3,5,9,12]`, `target = 9`  
**Output**: `4`  
**Explanation**: `9` exists in `nums` and its index is `4`.

### Example 2:
**Input**: `nums = [-1,0,3,5,9,12]`, `target = 2`  
**Output**: `-1`  
**Explanation**: `2` does not exist in `nums`, so return `-1`.

## Constraints:
- `1 <= nums.length <= 10^4`
- `-10^4 < nums[i], target < 10^4`
- All the integers in `nums` are unique.
- `nums` is sorted in ascending order.

---

## Solution:
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1
        while l <= r:         
            m = (l + r) // 2         ##for memory reasons we can change is as m = l + ((r - l) // 2)
            if nums[m] > target:
                r = m - 1
            elif nums[m] < target:
                l = m + 1
            else:
                return m
        return -1
```

### Explaination:
- Binary search algorithm finds the `mid`, `left` and `right`. Since the numbers are in ascending order we find if the the target is equal to mid or less than mid or more than mid. So if the target = mid then we found our element. if target < mid, then we can elliminate the right part of the array as we know it lies before mid. after this we find the mid of this shortened array again and soo on.  if target > mid, then we can elliminate the left part of the array as we know it lies after mid. after this we find the mid of this shortened array again and soo on. Until we find the element or not find the array. 
- Time complexity : `O(log n)`
- Space complexity : `O(1)`

link: https://youtu.be/s4DPM8ct1pI?si=7Fgy62VVu6VmU0cc
