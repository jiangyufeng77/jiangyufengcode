# 问题

 给定字符串J 代表石头中宝石的类型，和字符串 S代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。

J 中的字母不重复，J 和 S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。

# 程序
```python3
class Solution:
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        count = 0
        for i in range(len(S)):
            if S[i] in J:
                count += 1
        return count
```
# 心得
题目可以转变成看J中有几个S的字符。对于S字符串遍历，挨个和J中的字符比较，如果S[i]可以在J中找到，则count加1，最终返回count。