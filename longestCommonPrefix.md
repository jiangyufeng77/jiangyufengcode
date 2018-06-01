# 问题
编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。
# 程序
```C
char* longestCommonPrefix(char** strs, int strsSize) {
    int i,j;
    if(strsSize == 0)
    {
        return "";
    }
    for(i = 1; i < strsSize; i++)
    {
        for(j = 0; strs[0][j] != '\0'; j++)
        {
            if(strs[i][j] != strs[0][j])
            {
                strs[0][j] = '\0';
                break;
            }
        }
    }
    return strs[0];
}
```
# 心得
如果数组长为0，返回“”。如果数组不为空，则以第一行的字符串为基准，从第二行开始，依次将数与第一行对应的数相比较，如果不同，就将第一行中相应位置置0并终止循环。最终返回第一行中不为空的数。


