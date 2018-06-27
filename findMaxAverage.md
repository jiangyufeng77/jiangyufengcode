# 问题
给定 n 个整数，找出平均数最大且长度为 k 的连续子数组，并输出该最大平均数。
# 程序
```C
double findMaxAverage(int* nums, int numsSize, int k) {
    int i;
    int sum1 = 0, sum2 = 0;
    for(i = 0; i < k; i++)
    {
        sum1 += nums[i];
    }
    sum2 = sum1;
    for(i = k; i < numsSize; i++)
    {
        sum2 += nums[i] - nums[i - k];
        if(sum2 > sum1)
        {
            sum1 = sum2;
        }
    }
    return (double)sum1 / k;
}
```
# 心得
先求得前k个数的和sum1，求完后赋值给sum2，用于求后面的和。然后从第k个值开始，求k个数的和sum2，所用方法是加上最新的数，减去最开始的数，将新求得的和sum2和之前的和sum1对比，大的赋值给sum1，继续比较，最终返回平均值，强制转换成double型。