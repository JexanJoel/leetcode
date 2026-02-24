# LeetCode 112 - Path Sum

## Problem Description
Given the root of a binary tree and an integer `targetSum`, return `true` if the tree has a **root-to-leaf path** such that adding up all the values along the path equals `targetSum`.  
A **leaf** is a node with no children.

## Examples
**Example 1:**  
Input: root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22  
Output: true  
Explanation: The root-to-leaf path with the target sum is: 5 → 4 → 11 → 2  

**Example 2:**  
Input: root = [1,2,3], targetSum = 5  
Output: false  

**Example 3:**  
Input: root = [], targetSum = 0  
Output: false  

## Constraints
- The number of nodes in the tree is in the range `[0, 5000]`.
- `-1000 <= Node.val <= 1000`
- `-1000 <= targetSum <= 1000`

## Approach
Use **recursive DFS**:

1. **Base Case:**  
   - If the node is `null`, return `false`.  
   - If the node is a leaf, check if `node.val === targetSum`.

2. **Recursive Case:**  
   - Subtract `node.val` from `targetSum`.  
   - Recursively check left and right child.  
   - Return `true` if either child returns `true`.

## JavaScript Solution
```javascript
function hasPathSum(root, targetSum) {
    if (!root) return false; // empty tree
    
    // Leaf node
    if (!root.left && !root.right) {
        return root.val === targetSum;
    }
    
    const remainingSum = targetSum - root.val;
    return hasPathSum(root.left, remainingSum) || hasPathSum(root.right, remainingSum);
}