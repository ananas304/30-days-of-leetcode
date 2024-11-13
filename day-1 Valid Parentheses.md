# 20. Valid Parentheses  `Easy` `Commonly asked`
link: https://leetcode.com/problems/valid-parentheses/

- Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:
- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.
- Every close bracket has a corresponding open bracket of the same type.

## Examples:  
### Example 1:
**Input**: `s = "()"`  
**Output**: `true`

### Example 2:
**Input**: `s = "()[]{}"`  
**Output**: `true`

### Example 3:
**Input**: `s = "(]"`  
**Output**: `false`

### Example 4:
**Input**: `s = "([])"`  
**Output**: `true`

## Constraints:
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
- We use `stack` cause we have to pop the parentheses at the top of the list. for example we have [ ( ) ] that is the first element is "[" and the last element is "]" so first we check if the first characters is a `closing parentheses` if yes then we check if the `closing parentheses` has a coresponding `opening parentheses` in the stack(in correct order) then we pop the correspinding matching parentheses and the output would be `true` if there is no corresoinding has no macth then we return `false`, if it is a `opening parentheses` then we append/add it back to the stack
- we have [ ( ) ], first two chars are not `closing parentheses` so they are appended. the third char is a `closing parentheses` and the stack is not empty so it checks the hash map what is the corresponding `opening parentheses` to the `closing parentheses`, if it macthes that is in this case it does both "(", ")" are poped from the stack. same operation is done for the fourth character. Until the stack is empty. if the stack is empty we get `true` else we get `false`
  
- How do we know what closing parentheses match the corresponding opening parentheses, we use a `hashmap` to keep track.
  |  Hash | map   |
  |-------|-------|
  |   )   |   (   |
  |   ]   |   [   |
  |   }   |   {   |
  

#### Why this works: 
Time complexity and space Complexity are both `O(n)`

link: https://youtu.be/WTzjTskDFMg?si=Y-KU_PD0jE1qiObq
