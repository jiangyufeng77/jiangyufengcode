# 问题
给定一个单词列表，只返回可以使用在键盘同一行的字母打印出来的单词。
# 程序
```Python
class Solution(object):
    def findWords(self, words):
        """
        :type words: List[str]
        :rtype: List[str]
        """
        set1 = {"Q", "W", "E", "R", "T", "Y", "U", "I", "O", "P"}
        set2 = {"A", "S", "D", "F", "G", "H", "J", "K", "L"}
        set3 = {"Z", "X", "C", "V", "B", "N", "M"}
        res = []
        for i in words:
            test_set = set(i.upper())
            if test_set.issubset(set1) or test_set.issubset(set2) or test_set.issubset(set3):
                res.append(i)
        return res
```

# 心得
将三行键盘行分别定义为三个set，用res存放最终结果，upper函数的作用是将字符串中的小写字母转换成大写字母，并返回小写字母转成大写字母的字符串，test_set.issubset(set1)判断集合set1是否是集合test_set的子集，如果是子集，加到res中，set2和set3类似，最终返回res
