# 问题
给定一个整数，写一个函数来判断它是否是 2 的幂次方。
# 程序
```C
bool isPowerOfTwo(int n) {
    if(n == 1)
    {
        return true;
    }
    else if(n == 0 || n % 2 != 0)
    {
        return false;
    }
    else if((n % 2 == 0) && (n / 2 == 1))
    {
        return true;
    }
    else
    {
        return isPowerOfTwo(n / 2);
    }
}
```
# 心得
因为能被2整除的不一定是2的幂，但是不能被2整除的一定不是2的幂，所以返回false。对于可以被2整除的数，只有既能被2整除，商又是1的时候（即n=2）的时候才能返回true，否则就除以2后继续循环。