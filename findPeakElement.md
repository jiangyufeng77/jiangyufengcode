# 问题
峰值元素是指其值大于左右相邻值的元素。

给定一个输入数组 nums，其中 nums[i] ≠ nums[i+1]，找到峰值元素并返回其索引。

数组可能包含多个峰值，在这种情况下，返回任何一个峰值所在位置即可。

你可以假设 nums[-1] = nums[n] = -∞。

# 程序
```C
int findPeakElement(int* nums, int numsSize) {
    int i;
    int flag = 1;
    if((nums == NULL) && (numsSize == 0))
        return -1;
    for(i = 1; i < numsSize; i++)
    {
        if(flag && (nums[i] < nums[i - 1]))
            return i - 1;
        flag = nums[i] > nums[i - 1];
    }
    if(flag) 
        return numsSize - 1;
    return -1;
}
```
# 心得
如果数组为空，则返回-1，否则，从数组的第二个数开始，比较nums[i]和比它小的数，看flag和表达式是否同时成立，如果成立，说明是峰值，返回i-1，给flag赋上新的值，flag中的nums[i]和nums[i-1]与上一个if语句中的，不代表同一个i。如果for循环结束后，flag依旧为1，说明最后一个数比钱一个数大，也是一个峰值。