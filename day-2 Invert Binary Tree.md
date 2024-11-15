# 226. Invert Binary Tree `Easy`
link: https://leetcode.com/problems/invert-binary-tree

- Given the root of a binary tree, invert the tree, and return its root.

## Examples

### Example 1:
![Example 1](https://assets.leetcode.com/uploads/2021/03/14/invert1-tree.jpg)</br>
**Input**: `root = [4,2,7,1,3,6,9]`  
**Output**: `[4,7,2,9,6,3,1]`  

### Example 2:
![Example 2](https://assets.leetcode.com/uploads/2021/03/14/invert2-tree.jpg)</br>
**Input**: `root = [2,1,3]`  
**Output**: `[2,3,1]`  

### Example 3:
**Input**: `root = []`  
**Output**: `[]`

## Constraints:
- The number of nodes in the tree is in the range `[0, 100]`.
- `-100 <= Node.val <= 100`

---

## Solutions:
```python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return None
        
        #swap the children
        tmp = root.left
        root.left = root.right
        root.right = tmp

        self.invertTree(root.left)
        self.invertTree(root.right)
        return root
```

### Explainations:
- We can use DFS to recurvisely invert the tree. 

link: https://youtu.be/OnSn2XEQ4MY?si=_ypNRXWV1D7CsN-S
