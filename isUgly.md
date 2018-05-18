# 问题
编写一个程序判断给定的数是否为丑数。

丑数就是只包含质因数 2, 3, 5 的正整数。
# 程序
```C
bool isUgly(int num) {
    if(num <= 0) 
        return false;
    while(num > 1)
    {
    	if(!(num % 2)) 
            num /= 2;
    	else if(!(num % 3)) 
            num /= 3;
    	else if(!(num % 5)) 
            num /= 5;
    	else 
            return false;
    }
    return true;
}
```
# 心得
小于0的数，不是丑数。1是丑数。大于1的数，看它是否能被2，3，5求余后不为0，如果不为0，则分别除以2，3，5，继续循环。这样会使得最终返回true的数的质因数只包含2，3，5.