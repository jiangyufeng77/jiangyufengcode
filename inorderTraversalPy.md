# 问题
给定一个二叉树，返回它的中序遍历。
# 程序
```Python
class Solution(object):
    def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        res = []
        if root:
            if root.left:
                res = res + self.inorderTraversal(root.left)
            res.append(root.val)
            if root.right:
                res = res + self.inorderTraversal(root.right)
        return res
```
# 心得
中序遍历的顺序是根、左、右。如果根不为空，那先从它的左子树开始加入到res列表中，到左子树时，再考虑以它为根的情况下，再添加新的左子树和右子树，即将上一级的左子树作为根进入循环。然后再从右子树开始添加。以此类推。      