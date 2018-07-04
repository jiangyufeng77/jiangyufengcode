# 问题
给定一个包含非负整数的 m x n 网格，请找出一条从左上角到右下角的路径，使得路径上的数字总和为最小。

说明：每次只能向下或者向右移动一步。
# 程序
```C
int minPathSum(int** grid, int gridRowSize, int gridColSize) {
    int i,j;
    int sum;
    for(i = 1; i < gridRowSize; i++)
    {
        grid[i][0] += grid[i-1][0];
    }
    for(j = 1; j < gridColSize; j++)
    {
        grid[0][j] += grid[0][j-1];
    }
    for(i = 1; i < gridRowSize; i++)
    {
        for(j = 1; j < gridColSize; j++)
        {
            sum = grid[i-1][j] < grid[i][j-1] ? grid[i-1][j] : grid[i][j-1] ; 
            grid[i][j] += sum;
        }
    }
    return grid[gridRowSize-1][gridColSize-1];
}
```
# 心得
先用两个for循环使得第一排和第一列的数，每个都是自身和前一个数的总和，新得到的和数赋值到原位置上。然后从grid[1][1]开始，每两个数比较，取较小的数加到新位置上，再比较，最终在数组右下角得到最小路径和。