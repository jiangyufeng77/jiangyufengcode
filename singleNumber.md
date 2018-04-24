# 问题
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。
# 程序
```C
int singleNumber(int* nums, int numsSize) {
    if(numsSize == 1)
    {
        return nums[0];
    }
    while(numsSize != 1)
    {
        nums[0] ^= nums[numsSize - 1];
        numsSize--;
    }
    return nums[0];
}
```
# 心得
可以通过按位异或运算符来找出单个数字。在异或操作中，数的二进制按位运算，相同为1，不同为0，将每个数逐个和第一个数异或，最终即可得单个数。