# 问题
给定一个非负整数组成的非空数组，在该数的基础上加一，返回一个新的数组。

最高位数字存放在数组的首位， 数组中每个元素只存储一个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。


# 程序
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize) {
    int i;
    int a = 1;
    for(i = digitsSize - 1; i >= 0; i--)
    {
        if(a == 0)
        {
            break;
        }
        if(digits[i] + a > 9)
        {
            a = 1;
        }
        else
        {
            a = 0;
        }
    }
    if(a == 0)
    {
        *returnSize = digitsSize;
    }
    else
    {
        *returnSize = digitsSize + 1;
    }
    int *array = malloc(sizeof(int)* (*returnSize));
    a = 1;
    for(i = digitsSize - 1; i >= 0; i--)
    {
        array[i] = (digits[i] + a) % 10;
        a = (digits[i] + a) / 10;
    }
    if(a == 1)
    {
        array[0] = 1;
    }
    return array;
}
```
# 心得
在原数组中，给每个元素加1，如果加1后使得此数大于9，代表要进位，a仍旧为1，只有在相加小于9的时候，a才为0，如果a为1，说明最高位有进位，将要输出的新数组长度要比原数组多1，否则就相同。对于定义的新数组，从最后一位开始输入，对原数组中的每个元素加a后求余，对有无进位都有效，a此时可以相当于借位，如果a最后为1，说明新数组的首位上存放1。