# 问题
在二维数组grid中，grid[i][j]代表位于某处的建筑物的高度。 我们被允许增加任何数量（不同建筑物的数量可能不同）的建筑物的高度。 高度 0 也被认为是建筑物。

最后，从新数组的所有四个方向（即顶部，底部，左侧和右侧）观看的“天际线”必须与原始数组的天际线相同。 城市的天际线是从远处观看时，由所有建筑物形成的矩形的外部轮廓。 请看下面的例子。

建筑物高度可以增加的最大总和是多少？

# 程序
```C
int maxIncreaseKeepingSkyline(int** grid, int gridRowSize, int *gridColSizes) {
    int i,j;
    int sum = 0;
    int *array1 = (int*)calloc(gridRowSize, sizeof(int));
    int *array2 = (int*)calloc((*gridColSizes), sizeof(int));
    for(i = 0; i < gridRowSize; i++)
    {
        for(j = 0; j < *gridColSizes; j++)
        {
            if(array1[i] < grid[i][j])
            {
                array1[i] = grid[i][j];
            }
        }
    }
    for(j = 0; j < *gridColSizes; j++)
    {
        for(i = 0; i < gridRowSize; i++)
        {
            if(array2[j] < grid[i][j])
            {
                array2[j] = grid[i][j];
            }
        }
    }
    for(i = 0; i < gridRowSize; i++)
    {
        for(j = 0; j < *gridColSizes; j++)
        {
            sum += (array1[i] < array2[j] ? array1[i] : array2[j]) - grid[i][j];
        }
    }
    return sum;
}
```

# 心得
新定义两个矩阵array1和array2，先从行开始遍历数组，array1中存放每行的最大值，然后从列开始遍历数组，array2中存放每列的最大值。最后遍历整个数组，对相对应的行列数比较，将小的数和数组中的元素相减，得到的差值存放到sum变量中，最终返回sum。