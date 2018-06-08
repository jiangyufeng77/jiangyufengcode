# 问题
给定一个非负索引k，其中k≤33，返回杨辉三角形的第k个索引行。

请注意，行索引从0开始。
# 程序
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* getRow(int rowIndex, int* returnSize) {
    int i,j,l;
    int* res1 = (int*)malloc(sizeof(int)*(rowIndex+1));
    int* res2 = (int*)malloc(sizeof(int)*(rowIndex+1));
    *returnSize = rowIndex + 1;
    for(i = 0;i <= rowIndex;i++)
    {
        res1[i] = 1;
        res2[i] = 1;        
    }
    for(i = 0;i <= rowIndex;i++)
    {
        for(j = 1;j < i;j++)
        {
            res1[j] = res2[j] + res2[j-1];  
        }
        for(l = 0;l < rowIndex + 1;l++)
        {
            res2[l] = res1[l];
        }
    }
    return res1;
}
```
# 心得
先用一个for循环，将两个新定义的结果数中的值都赋值为1，然后再用嵌套的for循环，将上一行的第j和j-1个数的和赋给下一行的第j个数中，如此得到杨辉三角。