# 问题
自除数 是指可以被它包含的每一位数除尽的数。

例如，128 是一个自除数，因为 128 % 1 == 0，128 % 2 == 0，128 % 8 == 0。

还有，自除数不允许包含 0 。

给定上边界和下边界数字，输出一个列表，列表的元素是边界（含边界）内所有的自除数。
# 程序
```Python
class Solution(object):
    def selfDividingNumbers(self, left, right):
        """
        :type left: int
        :type right: int
        :rtype: List[int]
        """
        numbers = list(range(left, right+1))
        res = []
        for i in range(len(numbers)):
            t = []
            for j in range(len(str(numbers[i]))):
                number = str(numbers[i])[j]
                if not int(number) == 0:
                    t.append(numbers[i] % int(number) == 0)
                if int(number) == 0:
                    t.append(False)
            if all(t):
                res.append(numbers[i])
        return res        
```
# 心得
numbers利用range函数，从left开始，直到right+1，计数到right。res用于存放最终结果，t用于存放中间结果。用number表示numbers的每一位，如果number不为0，就可以用来作被除数，如果numbers除以number为0，说明可以除尽。用两个for循环来完成。        