# 问题
实现 int sqrt(int x) 函数。

计算并返回 x 的平方根，其中 x 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。
# 程序
```C
int mySqrt(int x) {
    if(x < 2)
        return x;
    int first = 1;
    int end = x; 
    int mid = 0;
    while(first <= end)
    {
        mid = first + (end - first) / 2;
        if(mid == x / mid)
            return mid;
        if(mid < x / mid)
            first = mid + 1;
        else
            end = mid - 1;
    }
    return end;
}
```
# 心得
如果输入的数是小于2的数，即0和1，其平方根仍旧是其自身；当输入的数大于等于2的时候，设定三个新的变量，first、end和mid，当first小于end的时候，以中间值为界限，如果所给的数除以中间值正好等于中间值，说明输入的数是中间值mid的平方，返回mid，如果mid小于x/mid，可以让first赋值为mid加1，再代入循环，否则就end减一，代入循环，直到相等。