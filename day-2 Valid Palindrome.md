# 125. Valid Palindrome `Easy`
link: https://leetcode.com/problems/valid-palindrome/

- A phrase is a palindrome if, after converting all uppercase letters into lowercase and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.
- Given a string `s`, return `true` if it is a palindrome, or `false` otherwise.

## Examples

### Example 1:
**Input**: `s = "A man, a plan, a canal: Panama"`  
**Output**: `true`  
**Explanation**: "amanaplanacanalpanama" is a palindrome.

### Example 2:
**Input**: `s = "race a car"`  
**Output**: `false`  
**Explanation**: "raceacar" is not a palindrome.

### Example 3:
**Input**: `s = " "`  
**Output**: `true`  
**Explanation**: `s` is an empty string "" after removing non-alphanumeric characters.  
Since an empty string reads the same forward and backward, it is a palindrome.

## Constraints:
- `1 <= s.length <= 2 * 10^5`
- `s` consists only of printable ASCII characters.

---

## Solutions:
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        newStr = ""

        for  c in s:
            if c.isalnum():
                newStr += c.lower()
        return newStr == newStr[::-1]
```
the below solution does not use built in functions.
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        l, r = 0, len(s) -1

        while l < r:
            while l < r and not self.alphanumeric(s[l]):
                l += 1
            while r > l and not self.alphanumeric(s[r]):
                r -= 1
            if s[l].lower() != s[r].lower():
                return False
            l, r = l + 1, r - 1
        return True
    
    def alphanumeric(self, c):
        return (ord('A') <= ord(c) <= ord('Z') or 
                ord('a') <= ord(c) <= ord('z') or
                ord('1') <= ord(c) <= ord('9'))
```

### Explainations:
- we only consider *Alphanumeric characters*, so we ignore spaces and other symbols.
- We remove the non alphanumeric characters, we convert all the alphabets to lowercase and then check if the string is a palindrome.
- Creating another String to store the characters will take up extra space and when we reverse the string also uses extra memory and we also use built in functions.
- We can use pointers and ASCII values.
- We have `L` pointer on the first character and `R` pointer on the last character. if the charcter that `L` pointer is pointing to a non-alphanumeric Charcter then the `L` pointer is moved forward or is incremented. If it is a Aplhanumeric character then the character of `L` pointer and character of `R` pointer are compared and if they match the `L` pointer is incremented and `R` pointer is decremented.
- for this method the Time complexity is O(n) and Space complexity is O(1).

link: https://youtu.be/jJXJ16kPFWg?si=OZOlf685Tm2Cji4I
