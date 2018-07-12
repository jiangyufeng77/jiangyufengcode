# 问题
给定一个 n x n 矩阵，其中每行和每列元素均按升序排序，找到矩阵中第k小的元素。
请注意，它是排序后的第k小元素，而不是第k个元素。
# 程序
```C
int kthSmallest(int** matrix, int matrixRowSize, int matrixColSize, int k) {
    int i,j;
    int min = matrix[0][0];
    int max = matrix[matrixRowSize-1][matrixColSize-1];
    int mid = 0;
    int count = 0;
    while (min < max) 
    {
        mid = (min + max) / 2;
        for (i = 0; i < matrixRowSize && matrix[i][0] <= mid; i++) 
        {
            for (j = 0; j < matrixColSize; j++) 
            {
                if (matrix[i][j] <= mid) 
                {
                    count++;   
                }
            }
        }
        if (k <= count) 
        {
            max = mid;
        } 
        else 
        {
            min = mid + 1;
        }
        count = 0;
    }
    return min;
}
```
# 心得
用二分法做，找到左上角的最小值和右下角的最大值，然后求得中间值mid，从左上角开始循环，以第一列元素不超过mid为最大限度，比较每个数和mid的大小，如果小于中间数，则计数count加一，否则继续比较下一个，两个for循环结束后，如果k的值比计数小于或等于，说明找到的值超过了要求的值，将最大值将低为最小值，否则就是最小值增加，如果此时仍满足最小值小于最大值，则继续循环，否则返回最小值。