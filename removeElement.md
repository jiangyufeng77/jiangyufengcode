# 问题
 给定一个数组和一个值，就地移除该值的所有实例并返回新的长度。
 不要为其他数组分配额外的空间，您必须通过在O(1)额外内存中就地修改输入数组来完成此操作。
 元素的顺序可以改变。无论你在新的长度以外留下什么都没有关系。
 
# 程序

```C
int removeElement(int* nums, int numsSize, int val) {
   int i;
    for(i = 0;i < numsSize; i++)
    {
        if(nums[i] == val)
        {
            if(i != numsSize - 1)
            {
                nums[i] = nums[numsSize - 1];
                i--;
            }
            numsSize--;
        }
    }
    return numsSize;
}
```

# 心得
对数组从头进行比较，将符合需要删除的值用数组中最后一个值进行覆盖，同时将数组长度减一。再从头比较，不符合的值就留在数组中，符合的就进行覆盖，最终得到移除一个数值的数组长度。
