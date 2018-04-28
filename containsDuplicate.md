# 问题
给定一个整数数组，判断是否存在重复元素。

如果任何值在数组中出现至少两次，函数应该返回 true。如果每个元素都不相同，则返回 false。
# 程序
```C
bool containsDuplicate(int* nums, int numsSize) {
    int i,j;
    for(i=0;i<numsSize;i++)
    {
        for(j=i+1;j<numsSize;j++)
        {
            if(nums[i]==nums[j])
            {
                return true;
            }
        }
    }
    return false;
}
```
# 心得
这个也是一个通过遍历挨个比较的题。从第一个数开始，依次和后面的数比较爱，如果有重复的，就返回true，没有就进行第二轮比较，直到每个都比较完才结束。