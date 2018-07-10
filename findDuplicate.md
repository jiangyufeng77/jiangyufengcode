# 问题
给定一个包含 n + 1 个整数的数组 nums，其数字都在 1 到 n 之间（包括 1 和 n），可知至少存在一个重复的整数。假设只有一个重复的整数，找出这个重复的数。
# 程序
```C
int findDuplicate(int* nums, int numsSize) {
    int i,j,t;
    if(numsSize == 0)
        return 0;
    if(((numsSize == 2) && (nums[0] == nums[1])) || numsSize == 1)
        return nums[0];
    for(i = 0; i < numsSize - 1; i++)
    {
        for(j = i + 1; j < numsSize; j++)
        {
            if(nums[i] == nums[j])
                t = nums[i];
        }
    }
    return t;
}
```
# 心得
对于数组长度为0的数，返回0；数组长度为1，或数组长度为2，但是两个元素相等的数组，都返回第一个数；长度超过2的数组，用两个for循环找相同的元素并赋值给t，最终返回t。