# 问题
假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。

请找出其中最小的元素。

你可以假设数组中不存在重复元素。
# 程序
```C
int findMin(int* nums, int numsSize) {
    int i;
    int min = nums[0];
    for(i = 1; i < numsSize; i++)
    {
        if(min > nums[i])
            min = nums[i];
    }
    return min;
}
```
# 心得
即使数组中元素的位置改变，但是最小值依旧是最小值，所以新定义一个变量min，用for循环从数组的第二位开始依次和min比较，将较小的值赋值给min，最终返回min。