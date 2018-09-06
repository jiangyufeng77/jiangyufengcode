# 问题
给定一个N叉树，找到其最大深度。

最大深度是指从根节点到最远叶子节点的最长路径上的节点总数。
# 程序
```Python
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: Node
        :rtype: int
        """
        if not root:
            return 0
        deep = 0
        for i in root.children:
            deep = max(deep, self.maxDepth(i))
        return deep + 1
```
# 心得
从根开始计数，如果不是根，则清0。新设定一个变量deep，用于存放深度，在根下循环，比较deep中存放的数和此时的深度，将较大值赋值给deep，最终返回deep + 1。        