# 问题
给定一个二进制矩阵 A，我们想先水平翻转图像，然后反转图像并返回结果。

水平翻转图片就是将图片的每一行都进行翻转，即逆序。例如，水平翻转 [1, 1, 0] 的结果是 [0, 1, 1]。

反转图片的意思是图片中的 0 全部被 1 替换， 1 全部被 0 替换。例如，反转 [0, 1, 1] 的结果是 [1, 0, 0]。
# 程序
```Python
class Solution(object):
    def flipAndInvertImage(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        for i in range(0, len(A)):
            A[i] = A[i][::-1]
            for n, j in enumerate(A[i]):
                if j ==1:
                    A[i][n] = 0
                else:
                    A[i][n] = 1
        return A
```
# 心得
两个for循环分别实现了两个目标，内层的for循环，完成反转图片的功能，使得在0的地方换成1，在1的地方换成0。外层的for循环完成水平翻转的功能。