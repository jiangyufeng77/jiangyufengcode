# 问题
给定两个字符串 s 和 t，判断它们是否是同构的。

如果 s 中的字符可以被替换得到 t ，那么这两个字符串是同构的。

所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。
# 程序
```C
bool isIsomorphic(char* s, char* t) {
    int i;
    int ls = strlen(s);
    int lt = strlen(t);
    for(i = 0; i < ls; i++)
    {
        if((strchr(s,s[i]) - s) != (strchr(t,t[i]) - t))
        {
            return false;
        }
    }
    return true;
}
```
# 心得
strchr函数的功能是查找字符串s中首次出现c字符的位置，返回首次出现c的位置的指针。从第一个字符开始循环，如果s第一次出现此字符的位置和t第一次出现此字符的位置不一样，返回false，否则返回true。