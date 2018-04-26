# 问题
给定一个Excel表格中的列名称，返回其相应的列序号。
# 程序
```C
int titleToNumber(char* s) {
    int res = 0;
    while(*s)
    {
        res = res * 26 + (*s - 'A' + 1);
        *s++;
    }
    return res;
}
```
# 心得
本题相当于是一个26进制，将每个字母和A进行比较，差值加一，即得这个字母对应的数字。