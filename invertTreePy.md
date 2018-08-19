# 问题
翻转一棵二叉树。
# 程序
```Python
class Solution(object):
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        q = collections.deque([(root)])
        while q:
            node = q.popleft()
            if node:
                node.left, node.right = node.right, node.left
                q.append(node.left)
                q.append(node.right)
        return root
```
# 心得
collections是Python内建的一个集合模块，提供了许多有用的集合类。deque模块是collections中的一项. 它提供了两端都可以操作的序列, 这意味着, 可以在序列前后都执行添加或删除，适合用于队列和栈。      
        