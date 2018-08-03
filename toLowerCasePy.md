# 问题
实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。
# 程序
```
class Solution(object):
    def toLowerCase(self, str):
        """
        :type str: str
        :rtype: str
        """
        s = ""
        for i in str:
            if  ord(i) >= ord ('A') and ord(i) < ord('a'):
                s += chr(ord(i) + 32)
            else:
                s += i
        return s
```
# 心得
Python中ord()函数是chr()函数的配对函数，它以一个字符（长度为1的字符串）作为参数，返回对应的ASCII值。