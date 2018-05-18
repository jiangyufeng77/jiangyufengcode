# 问题
给定两个没有重复元素的数组 nums1 和 nums2 ，其中nums1 是 nums2 的子集。找到 nums1 中每个元素在 nums2 中的下一个比其大的值。

nums1 中数字 x 的下一个更大元素是指 x 在 nums2 中对应位置的右边的第一个比 x 大的元素。如果不存在，对应位置输出-1。
# 程序
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* nextGreaterElement(int* findNums, int findNumsSize, int* nums, int numsSize, int* returnSize) {
    int i,j;
    int flag = 0;
    int* res = (int*)malloc(sizeof(int)*findNumsSize);
    *returnSize = findNumsSize;
    for(i = 0;i < findNumsSize;i++)
    {
        res[i] = -1;
    }
    for(i = 0;i < findNumsSize;i++)
    {
        flag = 0;
        for(j = 0;j < numsSize;j++)
        { 
            if(flag == 1 )
            {
                if(nums[j] > findNums[i])
                {
                    res[i] = nums[j];
                    break;
                }
            }
            if(findNums[i] == nums[j])
                flag = 1;
        }
    }
    return res;
}
```
# 心得
设定一个数组存放结果，根据题意，先全赋值为-1。然后在两个数组中遍历寻找相同的两个数，并设定flag=1，然后在第二个数组中，继续往下寻找大的数，如果找到了，赋值到结果数组的相应位置，并终止循环，开始新一轮，直到遍历结束。