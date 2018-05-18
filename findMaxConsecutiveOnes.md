# 问题
给定一个二进制数组， 计算其中最大连续1的个数
# 程序
```C
int findMaxConsecutiveOnes(int* nums, int numsSize) {
    int i;
    int max = 0, t = 0;
    for(i = 0;i < numsSize;i++)
    {
        if(nums[i] == 1)
        {
            t++;
        }
        else
        {
            if(t > max)
            {
                max = t;
            }
            t = 0;
        }
    }
    if(t > max)
    {
        max = t;
    }
    return max;
}
```
# 心得
设定一个可以存放最大值和中间值的变量，对数组遍历，如果数为一，则中间变量t加一，这样就可以得到此时连续的1的个数，当下一个数为0的时候，比较中间值和最大值，取最大的。