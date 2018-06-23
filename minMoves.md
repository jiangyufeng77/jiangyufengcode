# 问题
给定一个长度为 n 的非空整数数组，找到让数组所有元素相等的最小移动次数。每次移动可以使 n - 1 个元素增加 1。
# 程序
```C
int minMoves(int* nums, int numsSize) {
    int i;
    int min = nums[0];
    int count = 0;
    for(i = 1; i < numsSize; i++)
    {
        if(min > nums[i])
        {
            min = nums[i];
        }
    }
    for(i = 0; i < numsSize; i++)
    {
        count += nums[i] - min;
    }
    
    return count;
}
```
# 心得
先用for循环找到最小值，因为每次移动会使n-1个元素加1，所以移动的次数可以通过数值与最小值的差值和来确定。