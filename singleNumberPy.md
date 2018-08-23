# 问题
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现了三次。找出那个只出现了一次的元素。

# 程序
```Python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        s1 = sum(nums)
        s2 = sum(set(nums))
        s = s2 * 3 - s1
        s /= 2
        return s
        
```
# 心得
sum是求和函数，set是集合。以[2,2,3,2]为例，sum(nums)的结果为2 + 2 + 3 + 2 = 9，sum(set(nums))的结果为2 + 3 = 5。5 * 3 - 9 = 6。6 / 2 = 3就可以得到只出现一次的元素。        