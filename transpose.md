# 问题
给定一个矩阵 A， 返回 A 的转置矩阵。

矩阵的转置是指将矩阵的主对角线翻转，交换矩阵的行索引与列索引。
# 程序
```python
class Solution(object):
    def transpose(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        n_col = len(A)
        n_row = len(A[0])
        output = [[[]for a in range(n_col)] for b in range(n_row)]

        for i in range(n_col):
            for j in range(n_row):
                output[j][i] =A[i][j]
        return output
```
# 心得
定义一个行索引和列索引，用两个for循环来使得行和列的索引对换。        