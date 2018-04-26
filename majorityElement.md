# 问题
给定一个大小为 n 的数组，找到其中的众数。众数是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在众数。
# 程序
```C
int majorityElement(int* nums, int numsSize) {
    int i,t;
    int count=0;
    for(i=0;i<numsSize;i++)
    {
        if(count==0)
        {
            t=nums[i];
            count++;
        }
        else
        {
            if(t==nums[i])
            {
                count++;
                if(count>numsSize/2)
                    return t;
            }
            else
            {
                count--;
            }
        }
    }
    return t;
}
```
# 心得
对整个数组遍历，当计数为0的时候，中间值就等于此时i所对应的数组的值，再进行下一个比较。如果下一个数和中间值相等，则计数加一，并检查计数是否大于数组长度的一半，否则减一。