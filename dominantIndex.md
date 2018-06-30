# 问题
在一个给定的数组nums中，总是存在一个最大元素 。

查找数组中的最大元素是否至少是数组中每个其他数字的两倍。

如果是，则返回最大元素的索引，否则返回-1。
# 程序
```C
int dominantIndex(int* nums, int numsSize) {
    int max = 0;
    int second = 0;
    int i,j;
    for(i = 0; i < numsSize; i++)
    {
        if(nums[i] > max)
        {
            max = nums[i];
            j = i;
        }
    }
    for(i = 0; i < numsSize; i++)
    {
        if(i != j && nums[i] > second)
        {
            second = nums[i];
        }
    }
    if(max >= 2 * second)
    {
        return j;
    }
    return -1;
}
```
# 心得
先用for循环，找到数组中的最大元素，要看此最大元素是否是其它元素的二倍，可以看它是否是第二大的元素的二倍，因此再用一个for循环找到第二大的元素，如果最大的元素大于等于第二大的元素的二倍，则返回索引，否则返回-1.