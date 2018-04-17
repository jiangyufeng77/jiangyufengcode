# 问题
给定一个数组nums，编写一个函数将所有0移动到它的末尾，同时保持非零元素的相对顺序。

# 程序
```C
void moveZeroes(int* nums, int numsSize) {
    int i;
    int j=0;
    int zero=0;
    for(i=0;i<numsSize;i++)
    {
        if(nums[i]!=0)
        {
            nums[j]=nums[i];
            j++;
        }
    }
    for(j;j<numsSize;j++)
    {
        nums[j]=0;
    }
    return nums[j];
}
```
# 心得
先对数组进行一次遍历，把不是0的数按顺序存放于数组[j]中，再从数组j开始到规定的长度为止进行赋值，全赋值为0，最终返回数组[j]。