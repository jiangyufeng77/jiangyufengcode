# 问题
给定一个单词，你需要判断单词的大写使用是否正确。

我们定义，在以下情况时，单词的大写用法是正确的：

全部字母都是大写，比如"USA"。
单词中所有字母都不是大写，比如"leetcode"。
如果单词不只含有一个字母，只有首字母大写， 比如 "Google"。
否则，我们定义这个单词没有正确使用大写字母。
# 程序
```Cbool detectCapitalUse(char* word) {
    int i;
    int count = 0, first = 0;
    for(i = 0;i < strlen(word);i++)
    {
        if(i == 0 && isupper(word[i]))
        {
            first = 1;
            count++;
        }
        else if(isupper(word[i]))
        {
            count++;
        }
    }
    if(first == 1 && count == 1)
        return true;
    else if(count == strlen(word) || count == 0)
        return true;
    else
        return false;
}
```
# 心得
isupper函数可以检测字母是否是大写字母。对单词进行遍历，顺序依次检查。如果首字母是大写字母，first=1，计数count加一，如果后面的字母是大写字母，则count加一。当首字母为一，且计数为一，表明单词中只有首字母是大写的，返回true；计数为单词长度（即所有字母均为大写）或是为0（只有一个单词，且为小写），返回true；否则返回false。