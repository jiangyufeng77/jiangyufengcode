# 问题
自除数 是指可以被它包含的每一位数除尽的数。
例如，128 是一个自除数，因为 128 % 1 == 0，128 % 2 == 0，128 % 8 == 0。
还有，自除数不允许包含 0 。
给定上边界和下边界数字，输出一个列表，列表的元素是边界（含边界）内所有的自除数。
# 程序
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* selfDividingNumbers(int left, int right, int* returnSize) {
    int i, j, k;
    int *p = (int*)malloc((right-left+2)*sizeof(int));
    int *q = p;
    for (i = left; i <= right; i++) 
    {
        for (j = i; j > 0; j /= 10) 
        {
            k = j % 10;
            if (k == 0 || i % k != 0) 
            {
                break;
            }
        }
        if (j == 0) 
        {
            *p = i;
            p++;
        }
    }
    *returnSize = p - q;
    return q;
}
```
# 心得
int * a=(int * )malloc(n* sizeof(int)); 表示定义一个int类型的指针变量a，并申请 n* sizeof(int)个字节（即4*n个字节）的存储空间。 对left到right中的每个数依次遍历，通过求余或求商，进而求得这个数中的每个数字，看其是否可以被整除，得到的自除数存储在新列表中返回。
