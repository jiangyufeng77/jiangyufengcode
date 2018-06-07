# 问题
有两个短数组nums1和nums2，将数组nums1整合到数组nums2中。
# 程序
```C
void merge(int* nums1, int m, int* nums2, int n) {
    int i;
    int count1 = 0,count2 = 0,count3 = 0;
    int *res = (int*)malloc(sizeof(int)*(m+n));
    while(count1 != m && count2 != n)
    {
        if(nums1[count1] < nums2[count2])
        {
            res[count3] = nums1[count1];
            count1++;
            count3++;
        }
        else
        {
            res[count3] = nums2[count2];
            count2++;
            count3++;
        }
    }
    while(count1 != m)
    {
        res[count3] = nums1[count1];
        count1++;
        count3++;
    }
    while(count2 != n)
    {
        res[count3] = nums2[count2];
        count2++;
        count3++;
    }
    for(i = 0;i < m + n;i++)
    {
        nums1[i] = res[i];
    }
    return nums1;
}
```
# 心得
因为两个数组是有序的，所以可以将两个数组中的数一一进行比较，如果都在有效数字m和n中，比较两个数的大小，小的一个输入到新定义的数组中，如果两个数组中有一个先结束，则将另一个数组的数依次输入到新数组中，新数组的长度是两个短数组的有效长度。最终将新数组的数全部赋值到nums1数组中。
