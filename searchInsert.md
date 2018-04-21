# 问题
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。
# 程序
```C
int searchInsert(int* nums, int numsSize, int target) {
    int i;
    if(target <= nums[numsSize - 1])
    {
        for(i = 0;i <= numsSize;i++)
        {
            if(target <= nums[i])
            {
                return i;
            }
        }
    }
    else if(target > nums[numsSize - 1])
    {
        return numsSize;
    }
    return numsSize;
}
```
# 心得
当目标值小于等于数组中最后一个值的时候，遍历比较目标值和数组中的值，返回索引。当目标值大于数组中最后一个值的时候，直接返回数组长度，即插入到最后一位。