# 问题
如果一个矩阵的每一方向由左上到右下的对角线上具有相同元素，那么这个矩阵是托普利茨矩阵。

给定一个 M x N 的矩阵，当且仅当它是托普利茨矩阵时返回 True。

# 程序
```C
bool isToeplitzMatrix(int** matrix, int matrixRowSize, int *matrixColSizes) {
    int i,j;
    for(i = 0; i < matrixRowSize -1; i++)
    {
        for(j = 0; j < *matrixColSizes -1; j++)
        {
            if(matrix[i][j] != matrix[i+1][j+1])
            {
                return false;
            }
        }
    }
    return true;
}
```
# 心得
每行每列挨个遍历，只有matrix[i][j]和matrix[i+1][j+1]相等，才算是对角相等，可以返回true,否则就是false.