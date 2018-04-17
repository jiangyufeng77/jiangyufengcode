# 问题
给出一个包含0，1，2，...，n中n个数的序列，找出0、、、n中没有出现在序列中的那个数。
# 程序
```C
int missingNumber(int* nums, int numsSize) {
    int i,j;
    int sum = (numsSize * (numsSize + 1)) / 2;
    for(i = 0;i < numsSize;i++)
    {
        j += nums[i];
    }
    return (sum - j);
}
```
# 心得
求得所有数的总和，然后对数组进行遍历，求出数组的总和，两个总和相减即可得到缺少的数。