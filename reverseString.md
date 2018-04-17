# 问题
编写一个将字符串作为输入的函数，并返回反转的字符串。

# 程序
```C
char* reverseString(char* s) {
    int l = strlen(s);
    int i, n = l / 2;
    char t;
    for(i = 0;i < n;i++)
    {
        t = s[i];
        s[i] = s[l-1-i];
        s[l-1-i] = t;
    }
    return s;
}
```
# 心得
输入一个字符串，先求得字符串的长度，然后从头开始将第一个和从后面开始的第一个进行对换，依次进行即可得到反转的字符串。