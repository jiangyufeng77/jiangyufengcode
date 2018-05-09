# 问题
给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。
# 程序
```C
int removeDuplicates(int* nums, int numsSize) {
    int i;
    int count = 1;
    int a = nums[0];
    if(numsSize == 0)
        return 0;
    for(i = 1;i < numsSize;i++)
    {
        if(nums[i] != a)
        {
            count++;
            a = nums[i];
            nums[count-1] = a;
        }
    }
    return count;
}
```
# 心得
对于删除重复元素的问题，可以让从数组中第一个数开始，相邻两个数相比较，如果不同，则计数加一，并使得数组中对应位置为新的不同的数，这样就使得最终得到的数组是一个没有重复元素的数组。