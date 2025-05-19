# [Invert Binary Tree](https://neetcode.io/problems/invert-a-binary-tree)

## 5/18/2025

It's been a minute, but I'm getting back into this in earnest. This strikes me as a problem with straigtforward recursive solution. Invert left and right, then run the function on the left and right node. If left and right are None, return.

What's funny is, to solve the example problems you just need to swap the root's left and right.

This is complexity O(n) where n is the number of nodes.

```python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        return invertRoot(root)


def invertRoot(root: Optional[TreeNode]) -> Optional[TreeNode]:
    if root and (root.left or root.right):
        root.left, root.right = invertRoot(root.right), invertRoot(root.left)
    return root
```

Huh, I find it very odd that none of the listed solutions are my recursive solution. They are all iterative.

Okay, so the video solution did use recursion. I did have a slight 'optimization' in that mine didn't require the tmp variable. However, I did needlessly create a seperate funciton. Which is pretty silly looking back at it. The signatures are the same and invertTree just returns `invertRoot(root)` :)
