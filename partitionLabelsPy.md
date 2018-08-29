# 问题
字符串 S 由小写字母组成。我们要把这个字符串划分为尽可能多的片段，同一个字母只会出现在其中的一个片段。返回一个表示每个字符串片段的长度的列表。

# 程序
```Python
class Solution(object):
    def partitionLabels(self, S):
        """
        :type S: str
        :rtype: List[int]
        """
        res = []
        lastIdx = {}       
        for idx in range(len(S)):
            lastIdx[S[idx]] = idx       
        start = 0
        last = lastIdx[S[0]]
        for idx in range(len(S)):
            last = max(last, lastIdx[S[idx]])
            if idx == last:
                res.append(idx - start + 1)
                start = idx + 1
        return res
```
# 心得
用res来存放最终结果，先遍历一次字符串S，将每个字符出现在最右侧的位置记下，因为在每个区间字符出现的左右边界一定小于等于这个区间的左右边界，因此再进行一次遍历，如果当前字符出现的右边界大于前面所有字符出现的右边界，则更新右边界，如果遍历到当前的下标等于右边界，则把左边界到右边界的长度加到res中，更新左边界为当前下标+1。