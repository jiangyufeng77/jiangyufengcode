# 问题
给定一个包含 m x n 个元素的矩阵（m 行, n 列），请按照顺时针螺旋顺序，返回矩阵中的所有元素。
# 程序
```C
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* spiralOrder(int** matrix, int matrixRowSize, int matrixColSize) {
    int i;
    int p = 0;
    int * res = (int*) malloc(sizeof(int)*matrixRowSize*matrixColSize);
    int up = 0, down = matrixRowSize - 1, left = 0, right = matrixColSize - 1;
    while((up <= down) || (left <= right))
    {
        if(up <= down)
        {
            for(i = left; i <= right; i++)
            {
                res[p++] = matrix[up][i];
            }
            up++;
        }
        if(left <= right)
        {
            for(i = up; i <= down; i++)
            {
                res[p++] = matrix[i][right];
            }
            right--;
        }
        if(up <= down)
        {
            for(i = right; i >= left; i--)
            {
                res[p++] = matrix[down][i];
            }
            down--;
        }
        if(left <= right)
        {
            for(i = down; i >= up; i--)
            {
                res[p++] = matrix[i][left];
            }
            left++;
        }
    }
    return res;
}
```
# 心得
设定一个新数组，长度是长×宽，即所有数的长度。从4个方向（左到右，上到下，右到左，下到上）找到数组对应位置，依次添加到新数组res中，每完成一个方向，都要让这个方向上的参数向中间靠拢，因此，up++, right--, down--, left++。直到左边比右边大或上边比下边大为止，返回新数组res。
