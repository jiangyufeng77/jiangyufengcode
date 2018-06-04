# 问题
实现 strStr() 函数。

给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。
# 程序
```C
int strStr(char* haystack, char* needle) {
    int i,j;
    int l1 = strlen(haystack);
    int l2 = strlen(needle);
    if(l2 == 0)
    {
        return 0;
    }
    for(i = 0,j = 0;i < l1; i++)
    {
        if(haystack[i] == needle[j])
        {
            j++;
        }
        else
        {
            i = i - j;
            j = 0;
        }
        if(j == l2)
        {
            return (i + 1 - j);
        }
    }
    
    return -1;
}
```
# 心得
如果needle字符串的长度为0，说明其为空，返回0。如果needle的长度不为空，对haystack和needle字符串循环，如果发现相同位置上有相同的字母，则j加一，继续循环，否则i回到上一数，再加一，j回到0，即needle字符串重新开始和haystack对比。