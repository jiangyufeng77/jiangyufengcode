# 问题
给出 n 代表生成括号的对数，请你写出一个函数，使其能够生成所有可能的并且有效的括号组合。
# 程序
```Python
class Solution(object):
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        res = ["()"]
        if n == 1:
            return res
        for i in range(1,n):
            res = list(set([i[0:k]+"()"+i[k:] for i in res for k in range(len(i))]))
        return res
```
# 心得
定义一个res，用于存放结果，它是一个列表。set持有一系列元素，这一点和list很像，但是set的元素没有重复，而且是无序的，这点和dict的key很像。