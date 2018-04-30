# 问题
两个整数之间的汉明距离指的是这两个数字对应二进制位不同的位置的数目。

给出两个整数 x 和 y，计算它们之间的汉明距离。


# 程序
```C
int hammingDistance(int x, int y) {
    int number = x ^ y;
    int distance = 0;
    while(number)
    {
        number = number & (number - 1);
        distance++;
    }
    return distance;
}
```
# 心得
可以用异或运算来做，相同为0.相异为1，得到number，对number进行循环，当number不为0的时候，number和number减一相与，将结果又赋值给number，同时distance加一，直到number为0终止。