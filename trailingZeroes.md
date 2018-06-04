# 问题
给定一个整数 n，返回 n! 结果尾数中零的数量。
# 程序
```C
int trailingZeroes(int n) {
    int count = 0;
	while (n > 4)
    {
        n /= 5;
        count += n;
    }
	return count;
}
```
# 心得
阶乘的时候，可以看出，从1乘到5，才会产生一个0，下一次，乘到10的时候，尾数上有2个0，以5为一段，整数除以5，看商，尾数上零的个数为商。