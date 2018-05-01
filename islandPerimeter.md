# 问题
给定一个包含 0 和 1 的二维网格地图，其中 1 表示陆地 0 表示水域。网格中的格子水平和垂直方向相连（对角线方向不相连）。整个网格被水完全包围，但其中恰好有一个岛屿（或者说，一个或多个表示陆地的格子相连组成的岛屿）。岛屿中没有“湖”（“湖” 指水域在岛屿内部且不和岛屿周围的水相连）。格子是边长为 1 的正方形。网格为长方形，且宽度和高度均不超过 100 。计算这个岛屿的周长。
# 程序
```C
int islandPerimeter(int** grid, int gridRowSize, int gridColSize) {
    int l = 0;
    int i,j;
    for(i = 0;i < gridRowSize;i++)
    {
        for(j = 0;j < gridColSize;j++)
        {
            if(grid[i][j] == 1)
            {    
                l += 4;
                if(j > 0 && grid[i][j] == grid[i][j-1])
                {
                    l -= 2;
                }
            }
        }
    }
    for(i = 0;i < gridColSize;i++)
    {
        for(j = 0;j < gridRowSize;j++)
        {
            if(grid[j][i] == 1)
            {
                if(j > 0 && grid[j][i] == grid[j-1][i])
                {
                    l -= 2;
                }
            }
        }
    }
    return l;
}
```
# 心得
当网格代表的数字是1的时候，就说明可以作为陆地，它的边会成为周长的一部分，可以先加上4，但是由于相邻两个陆地会有边界重合，导致周长减少2.从行和列分别进行遍历，对于是陆地的就加4，上下左右重合的就减2，最终得到总周长。