# 问题
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

说明：本题中，我们将空字符串定义为有效的回文串。
# 程序
```C
bool isPalindrome(char* s) {
    int l = strlen(s);
    char *p = s;
    char *q = s + l - 1;
    if(!l)
    {
        return true;
    }
    while(p < q)
    {
        if(!isalnum(*p))
        {
            p++;
            continue;
        }
        if(!isalnum(*q))
        {
            q--;
            continue;
        }
        if(tolower(*p++) != tolower(*q--))
        {
            return false;
        }
    }
    return true;
}
```
# 心得
定义两个指针，从字符串的两头分别开始比较。isalnum的作用是判断字符变量c是否为字母或数字，若是则返回非零，否则返回零。tolower是一种函数，功能是把字母字符转换成小写，非字母字符不做出处理。如果遇到不是字母的时候，指针后移或前移，不比较，等不为空的时候，将所有字母转变成小写字母比较，如果不同，返回false，否则返回true。