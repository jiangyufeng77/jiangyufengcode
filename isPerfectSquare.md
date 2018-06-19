# 问题
给定一个正整数 num，编写一个函数，如果 num 是一个完全平方数，则返回 True，否则返回 False。

注意：不要使用任何内置的库函数，如  sqrt。

# 程序
```C
bool isPerfectSquare(int num) {
    int i;
    if(num < 2)
    {
        return true;
    }
    for(i = 1; i <= num / 2; i++)
    {
        if(i * i == num)
        {
            return true;
        }
    }
    return false;
}
```
# 心得
平方数就是一个数和它自身相乘后得到的值，1是平方数，直接返回true，大于1的时候，从1开始循环，循环到一半就可以了，如果一个数和其自身相乘是num，返回true，否则返回false。