# 问题
给定一个正整数，检查他是否为交替位二进制数：换句话说，就是他的二进制数相邻的两个位数永不相等。
# 程序
```C
bool hasAlternatingBits(int n) {
    int a = n % 2;
    int b = n / 2;
    int c;
    while(b > 0)
    {
        c = b % 2;
        if(a == c)
            return false;
        a = b % 2;
        b = b / 2;
    }
    return true;
}
```
# 心得
根据十进制转二进制来编程，a为余数，b为商，在商大于0的时候，将之前所得的商再进行求余，对相邻两个余数进行比较，相同则返回false，不同则继续。