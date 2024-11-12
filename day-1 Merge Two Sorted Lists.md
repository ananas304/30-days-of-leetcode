# 21. Merge Two Sorted Lists  `Easy` 
link: https://leetcode.com/problems/merge-two-sorted-lists/<br/>
*Difficulty: Medium*

## Description:
You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

#### Example 1:
![Example 1](https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg)<br/>
**Input**: `list1 = [1,2,4]`, `list2 = [1,3,4]`  
**Output**: `[1,1,2,3,4,4]`

#### Example 2:
**Input**: `list1 = []`, `list2 = []`  
**Output**: `[]`

#### Example 3:
**Input**: `list1 = []`, `list2 = [0]`  
**Output**: `[0]`

### Constraints:
- The number of nodes in both lists is in the range `[0, 50]`.
- `-100 <= Node.val <= 100`
- Both `list1` and `list2` are sorted in non-decreasing order.

---

## Solution:
```python
1. class Solution:
2.    def mergeTwoLists(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
3.        dummy = ListNode()
4.        tail = dummy
5.        while l1 and l2:
6.            if l1.val < l2.val:
7.                tail.next = l1
8.                l1 = l1.next
9.            else:
10.               tail.next = l2
11.               l2 = l2.next
12.           tail = tail.next
13.       if l1:
14.           tail.next = l1
15.       elif l2:
16.           tail.next = l2
17.      return dummy.next
```
### Explanation:
To avoid the edge case of initial empty list we use `dummy` node. We have two lists. We compare each node of the two lists and append them to the output list mainting the sorted sequence. If there were some extra sequence of nodes in one of the list we would be appended to the output list as they are. 
**example 1:**
L1 : 1 -> 2 -> 4
L2 : 1 -> 3 -> 4
Output : Dummy -> 1 -> 1 -> 2 -> 3 -> 4 -> 4

**example 2:**
L1 : 1 -> 2 -> 4
L2 : 1 -> 3 -> 4 -> 5 -> 6 -> 7
Output : Dummy -> 1 -> 1 -> 2 -> 3 -> 4 -> 4  5 -> 6 -> 7

**Code**: 
2. We create a list called dummy
3. Tail of our list is dummy(avoid the edge case)
4. while l1 and l2 is not numm
13. if l1 is not null, then we take the remaining portions and inserting into the list 
14. elif l2 is not null, then we take the remaining portions and inserting into the list 

link: https://youtu.be/XIdigk956u0?si=X5z9TaGqQtPK2_du
