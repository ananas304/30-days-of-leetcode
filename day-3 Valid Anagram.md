# 242. Valid Anagram `Easy`
link: https://leetcode.com/problems/valid-anagram

**Given**: Two strings `s` and `t`.  
**Goal**: Return `true` if `t` is an anagram of `s`, and `false` otherwise.

## Examples

### Example 1:
**Input**: `s = "anagram"`, `t = "nagaram"`  
**Output**: `true`

### Example 2:
**Input**: `s = "rat"`, `t = "car"`  
**Output**: `false`

## Constraints:
- `1 <= s.length, t.length <= 5 * 10^4`
- `s` and `t` consist of lowercase English letters.

## Follow-Up:
What if the inputs contain Unicode characters?  
**Adaptation**: To handle Unicode, ensure you use data structures (e.g., `collections.Counter` in Python) or approaches that can handle Unicode characters, allowing counting and comparison of characters beyond basic ASCII.

---

## Solution:
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        
        countS, countT = {}, {}

        for i in range(len(s)):
            countS[s[i]] = 1 + countS.get(s[i], 0)
            countT[t[i]] = 1 + countT.get(t[i], 0)
        for c in countS:
            if countS[c] != countT.get(c, 0):
                return False

        return True
```

or use `Counter` ds in python that counts automatically

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return Counter(s) == Counter(t)
```

or use sorting method (space complexity: O(1) for some optimized sorted algos )

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return sorted(s) == sorted(t)
```

### Explanation:
- We can use arrays or hashmaps. We can store the number of letters in both s and t in hashmaps and compare.
- Time complexity: `O(S + T)`
- Time complexity: `O(S + T)`
- We can sort `t` and check if it matches `s`.

link: https://youtu.be/9UtInBqnCgA?si=UxhUmu88IFOXgT_s
 
