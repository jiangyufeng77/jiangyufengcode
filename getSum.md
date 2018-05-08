# 问题
不使用运算符 + 和-，计算两整数a 、b之和。
# 程序
```C
int getSum(int a, int b) {
    while (a & b) {
        a = a ^ b;
        b = ((a ^ b) & b) << 1;
    }
    return a ^ b;
}
```
# 心得
不用加减运算，可以用位运算来做。两数相与不为0的时候，a被赋值为a和b的异或，而b被赋值为a和b异或后再和b相与，然后左移一位，循环直到ab相与为0终止。