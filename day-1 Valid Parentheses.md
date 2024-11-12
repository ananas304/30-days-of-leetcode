# 20. Valid Parentheses  `Easy` `Commonly asked`
link: https://leetcode.com/problems/valid-parentheses/

## Hint:
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:
- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.
- Every close bracket has a corresponding open bracket of the same type.

#### Example 1:
**Input**: `s = "()"`  
**Output**: `true`

#### Example 2:
**Input**: `s = "()[]{}"`  
**Output**: `true`

#### Example 3:
**Input**: `s = "(]"`  
**Output**: `false`

#### Example 4:
**Input**: `s = "([])"`  
**Output**: `true`

### Constraints:
- `1 <= s.length <= 10^4`
- `s` consists of parentheses only `'()[]{}'`.

---

## Solution: 
```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        closeToOpen = {")" : "(", "]" : "[", "}" : "{" }
        for c in s:
            if c in closeToOpen:
                if stack and stack[-1] == closeToOpen[c]:
                    stack.pop()
                else:
                    return False
            else:
                stack.append(c)
        return True if not stack else False
```
### Explanation:
We use `stack` cause we have to pop the parentheses at the top of the list. for example we have [()] 
How do we know what closing parentheses match the corresponding opening parentheses, we use a `hashmap` to keep track. 
link: https://youtu.be/WTzjTskDFMg?si=Y-KU_PD0jE1qiObq
