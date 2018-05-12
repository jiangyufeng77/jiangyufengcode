# 问题
编写一个算法来判断一个数是不是“快乐数”。

一个“快乐数”定义为：对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和，然后重复这个过程直到这个数变为 1，也可能是无限循环但始终变不到 1。如果可以变为 1，那么这个数就是快乐数。
# 程序
```C
int Result(int n) {
    int t;
    int sum = 0;
    while (n) {
        t = n % 10;
        sum += t * t;
        n /= 10;
    }
    return sum;
}
bool isHappy(int n) {
    int a = n,b = n;
    do {
        a = Result(a);
        b = Result(b);
        b = Result(b);
    } while(a != b);
    if (a == 1) 
        return true;
    else 
        return false;
}
```
# 心得
Result运行后会得到一个数的每个数字的平方和，在第二个程序中可以直接引用。第二个程序中，a和b表示相邻两个平方和，可以先求出两个数，再进行比较，两个数不同，就循环求一次；两个数相同，代表这个循环可以终止了，再进行下去也没有意义。如果a=1，就返回true，如果不等，就返回false。