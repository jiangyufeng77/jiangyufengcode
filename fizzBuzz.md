# 问题
写一个程序，输出从 1 到 n 数字的字符串表示。

1. 如果 n 是3的倍数，输出“Fizz”；

2. 如果 n 是5的倍数，输出“Buzz”；

3.如果 n 同时是3和5的倍数，输出 “FizzBuzz”。
# 程序
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
char** fizzBuzz(int n, int* returnSize) {
    int i;
    char** result = malloc(sizeof(char*) * n);
    for(i = 0; i < n; i++)
        result[i] = malloc(sizeof(char) * n);
    for(i = 1; i < n+1; i++)
    {
        if(!(i % 3) && !(i % 5))
            sprintf(result[i-1], "FizzBuzz");
        else if(!(i % 3))
            sprintf(result[i-1], "Fizz");
        else if(!(i % 5))
            sprintf(result[i-1], "Buzz");
        else
            sprintf(result[i-1], "%d", i);
    }
    *returnSize = n;
    return result;
}
```
# 心得
新定义一个数组并对其依次赋值，然后用for循环找到既能被3整除又能被5整除的数，输出FizzBuzz；只能被3整除的数输出Fizz；只能被5整除的数输出Buzz，其余的数输出原数。