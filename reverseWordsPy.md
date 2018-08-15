# 问题
给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。
# 程序
```Python
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        s = s.split(' ')
        a = ''
        for i in s:
            a = a + i[::-1] + ' '
        return a[:len(a)-1]
```
# 心得
split() 通过指定分隔符对字符串进行切片，如果参数 num 有指定值，则仅分隔 num个子字符串，返回分割后的字符串列表。用a存放新的字符串，从一个单词的倒数一个字母开始存放进a。