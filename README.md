# Lowest Common Ancestor of Deepest Leaves

## Problem Statement
Given the root of a binary tree, return the **lowest common ancestor (LCA)** of its deepest leaves.

### Definitions:
- A node in a binary tree is a **leaf** if and only if it has no children.
- The depth of the root node is **0**. If a node has a depth of **d**, then its children's depth is **d + 1**.
- The **lowest common ancestor** (LCA) of a set **S** of nodes is the node **A** with the largest depth such that every node in **S** is in the subtree with root **A**.

## Example

### Example 1:
```
Input: root = [3,5,1,6,2,0,8,null,null,7,4]
Output: [2,7,4]
```
**Explanation:**
- The deepest leaf nodes are **7** and **4**, both at depth **3**.
- Their lowest common ancestor is **2**.

### Example 2:
```
Input: root = [1]
Output: [1]
```
**Explanation:**
- The root itself is the deepest node and hence its own LCA.

### Example 3:
```
Input: root = [0,1,3,null,2]
Output: [2]
```
**Explanation:**
- The deepest leaf node is **2**, so its LCA is itself.

## Constraints
- The number of nodes in the tree is **[1, 1000]**.
- `0 <= Node.val <= 1000`
- The values of the nodes are **unique**.

## Approach
1. Compute the **height** of the left and right subtrees.
2. If both have the **same height**, return the current node as LCA.
3. If one subtree is **deeper**, move towards that subtree recursively.

## Code Implementation
```java
class Solution {
    public TreeNode lcaDeepestLeaves(TreeNode root) {
        if (root == null) return null;
        int lh = height(root.left);
        int rh = height(root.right);
        if (lh == rh) return root;
        if (lh > rh) 
            return lcaDeepestLeaves(root.left);
        return lcaDeepestLeaves(root.right);
    }

    private int height(TreeNode root) {
        if (root == null) return 0;
        return 1 + Math.max(height(root.left), height(root.right));
    }
}
```


## Complexity Analysis
- **Height Calculation:** `O(N)` where `N` is the number of nodes.
- **Recursive LCA Calculation:** `O(N)`
- **Overall Complexity:** `O(N)`

## Contribution
Feel free to open issues and submit pull requests. Contributions are always welcome!



