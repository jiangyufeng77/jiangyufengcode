# 问题
给定一个仅包含大小写字母和空格 ' ' 的字符串，返回其最后一个单词的长度。

如果不存在最后一个单词，请返回 0 。

说明：一个单词是指由字母组成，但不包含任何空格的字符串。


# 程序
```C
int lengthOfLastWord(char* s) {
    int i = 0;
    int res = 0;
    int count = 0;
    while(s[i] != NULL)
    {
        if(s[i] == ' ')
        {
            count = 0;
        }
        else 
        {
            count++;
            res = count;
        }
        i++;
    }
    return res;
}
```
# 心得
从字符串的第一个字符开始循环，如果遇到了空格，则将计数count重新赋值为0，如果没有，则一直计数，并将计数的结果赋值给res，最终返回res。