# 问题
给定一个整数数组，其中第 i 个元素代表了第 i 天的股票价格 。​

设计一个算法计算出最大利润。在满足以下约束条件下，你可以尽可能地完成更多的交易（多次买卖一支股票）:

你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。
卖出股票后，你无法在第二天买入股票 (即冷冻期为 1 天)。
# 程序
```C
int maxProfit(int* prices, int pricesSize) {
    int i;
    int last, dlast, t;
	for(i = 1, dlast = 0, last = 0; i < pricesSize; i++)
	{
		t  = last;
		last  = last + prices[i] - prices[i-1] > dlast ? last + prices[i] - prices[i-1] : dlast ;
		dlast = t > dlast ? t : dlast;
	}
	return dlast > last ? dlast : last;
}
```
# 心得
从数组的第二个元素开始，逐次比较两个元素之间的差值，如果比dlast大，last就为其原来的值加上差值，就将dlast的值赋给last，取二者之间较大的值；然后用t，即原来的last和原来的dlast比较，返回较大的数并赋值给dlast。最终返回dlast和last中较大的数。这样才可以保证低价买入，高价卖出，且在卖出之后的冷冻期不会影响后续的买入。