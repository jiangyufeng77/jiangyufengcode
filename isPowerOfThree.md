# 问题
给定一个整数，写一个函数来判断它是否是 3 的幂次方。
# 程序
```C
bool isPowerOfThree(int n) {
    if(n == 0)
    {
        return false;
    }
    else if(n == 1 || n == 3 || n == 9)
    {
        return true;
    }
    else if(n % 9 != 0)
    {
        return false;
    }
    else
    {
        return isPowerOfThree(n / 9);
    }
}
```
# 心得
如果输入为0，不是3的幂；在个位数中，是3的幂的有1、3、9，个位数不是这三个，或是超过9以上的数，用9来求余，看是否可以被9整除，如果不可以，说明不是，否则就除以9，来进行下一轮的循环。