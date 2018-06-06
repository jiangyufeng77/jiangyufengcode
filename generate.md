# 问题
给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。
# 程序
```C
/**
 * Return an array of arrays.
 * The sizes of the arrays are returned as *columnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** generate(int numRows, int** columnSizes) {
    int i,j;
    int ** array =  (int *)(malloc(sizeof(int *)* numRows));     
    (*columnSizes) = (int *)(malloc (sizeof(int)* numRows));                     
    for (i = 0 ; i < numRows; i++)
    {
        (*columnSizes)[i] = i+1;
        array[i] =  (int *)(malloc(sizeof(int *)* i+1));
        for (j =0 ; j <= i; j++)
        {
             if ((j==0) || (j==i))
             {
                 array[i][j] = 1;
             }
             else
             {
                array[i][j] = array[i-1][j-1] + array [i-1][j];       
             } 
        }
     }                 
    return array;
}
```
# 心得
首先确定行的长度，嵌套循环，设定i=0，每行的长度都比i多一，然后设定j也从0开始，但是到i为止，如果j为0或j为i，说明此时指的是杨辉三角的两边，其值为1，如果不是，则其值为上一行左右两个数的和。