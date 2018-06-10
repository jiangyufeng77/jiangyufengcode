# 问题
给定一个整数数组nums，找到连续的子数组（包含至少一个数字），它具有最大的总和并返回其总和。
# 程序
```C
int maxSubArray(int* nums, int numsSize) {
    int i;
    int sum = nums[0];
    int res = sum;
    if(numsSize == 1)
    {
        return nums[0];
    }
    for(i=1;i < numsSize;i++)
    {
        if(sum <= 0)
        {
            sum = 0;
        }
        sum = sum + nums[i];
        if(res < sum)
        {
            res=sum;
        }
    }
    return res;
}
```
# 心得
如果数组长度为1，即只有一个字符，就返回此数；如果不为1，因为已将第一个数赋值给sum，所以从第二个数开始循环，如果总和小于等于0，说明这个数对下一轮的加法起反作用或不起作用，排除，所以sum从0开始重新计数求和，将结果数和总和比较，将大的值赋值给结果数，最终返回结果数。