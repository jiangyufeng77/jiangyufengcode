# 问题
给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。
# 程序
```C
void rotate(int* nums, int numsSize, int k) {
    int *res = malloc(sizeof(int)*numsSize);
    int i;
    int j = 0;
    while(k > numsSize)
    {
        k -= numsSize;
    }
    for(i = numsSize - k; i < numsSize; i++)
    {
        res[j++] = nums[i];
    }
    for(i = 0; i < numsSize - k; i++)
    {
        res[j++] = nums[i];
    }
    for(i = 0; i < numsSize; i++)
    {
        nums[i] = res[i];
    }
}
```
# 心得
旋转后得到的数组可以从中分成两部分，设定一个新的数组res，数组中的前半部分就是原数组的后半部分，用for循环把从numsSize-k个位置开始到最后的元素依次赋值到新数组的起始位置， 再用一个for循环，把从原数组起始位置到numsSize-k的元素依次加到res的后半部分。最后将res数组中的数依次赋值到nums数组。