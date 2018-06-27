# 问题
给定一个整数类型的数组 nums，请编写一个能够返回数组“中心索引”的方法。

我们是这样定义数组中心索引的：数组中心索引的左侧所有元素相加的和等于右侧所有元素相加的和。

如果数组不存在中心索引，那么我们应该返回 -1。如果数组有多个中心索引，那么我们应该返回最靠近左边的那一个。
# 程序
```C
int pivotIndex(int* nums, int numsSize) {
    int i;
    int sum1 = 0, sum2 = 0;
    if(numsSize == 0)
    {
        return -1;
    }
    for(i = 1; i < numsSize; i++)
    {
        sum2 += nums[i];
    }
    if(sum1 == sum2)
    {
        return 0;
    }
    for(i = 1; i < numsSize; i++)
    {
        sum1 += nums[i - 1];
        sum2 -= nums[i];
        if(sum1 == sum2)
        {
            return i;
        }
    }
    return -1;
}
```
# 心得
如果数组长度为0，返回-1。先用for循环将数组从第二个数开始求和，如果求得的和数sum2和sum1一样，都为0，则返回0。再用for循环，求得左边所有数的和以及右边所有数的和，如果两个和相等，则返回i，否则返回-1.