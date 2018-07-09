# 问题
在未排序的数组中找到第 k 个最大的元素。请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。
# 程序
```C
int findKthLargest(int* nums, int numsSize, int k) {
    int i,j,t;
    int target;
    if(((numsSize == 0) && (k == 0)) || ((numsSize == 1) && (k = 1)))
        return nums[0];
    for(i = 0; i < numsSize; i++)
    {
        for(j = i + 1; j < numsSize; j++)
        {
            if(nums[i] < nums[j])
            {
                t = nums[i];
                nums[i] = nums[j];
                nums[j] = t;
            }
        }
    }
    for(i = 0; i < k; i++)
    {
        target = nums[k - 1];
    }
    return target;
}
# 心得
对于空数组和长度为1的数组，最终都只返回这个元素或0。大于1个元素的数组，用两个for循环从数组的第一个元素开始，依次用它和后面所有的数比较，把较大的数交换赋值到此位置，最终得到一个降序排列的数组，返回这个数组的第k个数，即nums[k-1];