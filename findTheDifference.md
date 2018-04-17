# 问题

给定两个字符串s和t，它们只包含小写字母。

字符串t由随机洗牌字符串s生成，然后在随机位置添加一个字母。

找到在t中添加的字母。

# 程序

```c
char findTheDifference(char* s, char* t) {
    int i = 0, j = 0, a = 0, b = 0;
    char result;
    while(s[i])
    {
        a += s[i];
        i++;
    }
    while(t[j])
    {
        b += t[j];
        j++;
    }
    result = (char)(b - a);
    return result;
}

```

# 心得

对两个字符串分别遍历，对遍历后的结果进行比较，并定义为字符格式，最终得到不同的字符。
