# 问题
罗马数字包含以下七种字符：I， V， X， L，C，D 和 M。
I->1; V->5; X->10; L->50; C->100; D->500; M->1000。
给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。
# 程序
```C
int romanToInt(char* s) {
    int num = 0, pre = 0;
    int sum = 0;
    while(*s != '\0')
    {
        switch(*s)
        {
            case 'I': num = 1; break;
            case 'V': num = 5; break;
            case 'X': num = 10; break;
            case 'L': num = 50; break;
            case 'C': num = 100; break;
            case 'D': num = 500; break;
            case 'M': num = 1000; break;
        }
        sum += num;
        if(pre < num)
        {
            sum -= (pre * 2);
        }
        pre = num;
        s++;
    }
    return sum;
}
```
# 心得
先用switch语句，使得每个罗马字母都有数字对应。对每个罗马数字依次求和，但是新的和要减去上一个数字的两倍，最终返回和数。