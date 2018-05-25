# 问题
给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。

如果你最多只允许完成一笔交易（即买入和卖出一支股票），设计一个算法来计算你所能获取的最大利润。

注意你不能在买入股票前卖出股票。
# 程序
```C
int maxProfit(int* prices, int pricesSize) {
    int i;
    int t = prices[0];
    int res = 0;
    for(i = 1;i < pricesSize;i++)
    {
        if(t > prices[i])
        {
            t = prices[i];
        }
        else if(res < prices[i] - t)
        {
            res = prices[i] - t;
        }
    }
    return res;
}
```
# 心得
这道题的本质找到一个数，并在它的后面找到一个比它大的数，返回它俩的差值。先定义一个中间值t，并赋值为数组中的第一个数，然后用for循环从第二个数开始遍历数组，将中间值和数组中的值比较，如果中间值大，就把新值赋给t；如果两个数的差值比定义的结果值res大，将新值赋给res，最终返回res。