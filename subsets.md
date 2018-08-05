# 问题
给定一组不含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。

说明：解集不能包含重复的子集。

# 程序
```Python
class Solution(object):
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        subset = [[]]
        for i in nums:
        	temp = []
        	for j in subset:
        		temp.append(j + [i])
        	subset = subset + temp
        return subset
```

# 心得
append函数用于添加到列表末尾添加对象，用两个for循环，像一个空数组中添加数据。