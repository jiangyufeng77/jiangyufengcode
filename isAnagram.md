# 问题
给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的一个字母异位词。
# 程序
```C
bool isAnagram(char* s, char* t) {
    int i;
    int l = strlen(s);
    int a[26] = {0};
    if(l != strlen(t))
        return false;
    else
    {
        for(i = 0;i < l;i++)
        {
            a[s[i] - 'a']++;
            a[t[i] - 'a']--;
        }
        for(i = 0;i < 26;i++)
        {
            if(a[i] != 0)
                return false;
        }
    }
    return true;
}
```
# 心得
如果s和t都为空，就返回true。如果s和t长度不同，直接返回false。新建立一个数组，长度为26，赋值都为0，分别对s和t中的字母与字符a进行比较，一个加，一个减，如果是字母异位，则数组a中的数互相抵消，a[i]为0，返回true，否则，返回false。