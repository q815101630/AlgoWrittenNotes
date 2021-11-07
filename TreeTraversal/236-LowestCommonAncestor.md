# 236-LowestCommonAncestor

#### [Lowest Common Ancestor of a Binary Tree](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree/)



# 思路

太牛逼的递归了，我竟然没写过，我。。。

![image-20211106211737718](https://raw.githubusercontent.com/q815101630/pic_storage/main/img/image-20211106211737718.png)

```python

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if not root:
            return
        if root is p or root is q:
            return root
        
        left = self.lowestCommonAncestor(root.left, p, q)
        right = self.lowestCommonAncestor(root.right, p, q)

        if left and right:
            return root
        if not left:
            return right
        if not right:
            return left
        return
```



# 复杂度

时间O(n)

空间O(1)