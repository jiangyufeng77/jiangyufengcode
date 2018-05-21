# 问题
给定一个只包含小写字母的有序数组letters 和一个目标字母 target，寻找有序数组里面比目标字母大的最小字母。

数组里字母的顺序是循环的。举个例子，如果目标字母target = 'z' 并且有序数组为 letters = ['a', 'b']，则答案返回 'a'。
# 程序
```C
char nextGreatestLetter(char* letters, int lettersSize, char target) {
    int i;
    for(i = 0;i < lettersSize;i++)
    {
        if(letters[i] > target)
        {
            return letters[i];
        }
    }
    return letters[0];
}
```
# 心得
用for循环将整个数组中的数与目标数挨个比较，因为给定的数组是有序的，所以可以简单的按顺序比较，当检查到一个数比目标数大的时候，就输出这个字母，否则返回数组中的第一个字母。