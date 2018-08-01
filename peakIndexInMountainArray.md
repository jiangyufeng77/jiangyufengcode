# 问题
我们把符合下列属性的数组 A 称作山脉：

A.length >= 3
存在 0 < i < A.length - 1 使得A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1]
给定一个确定为山脉的数组，返回任何满足 A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1] 的 i 的值。

# 程序
```Python
class Solution(object):
    def peakIndexInMountainArray(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        l, r = 0, len(A) - 1
        while l < r:
            mid = (l + r) / 2
            if A[mid] < A[mid + 1]:
                l = mid
            elif A[mid - 1] > A[mid]:
                r = mid
            else:
                return mid
```
# 心得
本题是一个找最大值的题，因为整个数组的大小是先增大，后减小的，所以最大值大约在整个数组的中间部分。设定一个变量mid，l和r分别为数组的最大值和最小值，mid先取两个数的均值，如果数组中这个索引的数小于后一个，把中值赋给l，否则赋给r，返回mid。