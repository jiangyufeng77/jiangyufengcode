# 问题
给定一个字符串 S 和一个字符 C。返回一个代表字符串 S 中每个字符到字符串 S 中的字符 C 的最短距离的数组。
# 程序
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* shortestToChar(char* S, char C, int* returnSize) {
    int i;
    int l = strlen(S);
    int *res = malloc(sizeof(int)*l);
    for(i = 0;i < l;i++)
    {
        if(S[i] == C)
        {
            res[i] = 0;
        }
        else
        {
            res[i] = l;
        }
    }
    for(i = 1;i < l;i++)
    {
        if(res[i] > (res[i-1] +1))
        {
            res[i] = res[i-1] + 1;
        }
    }
    for(i = l - 2;i >= 0;i--)
    {
        if(res[i] > (res[i+1] + 1))
        {
            res[i] = res[i+1] + 1;
        }
    }
    *returnSize = l;
    return res;
}
```
# 心得
因为目标字母存在在字符串中，其左右都有别的字母，所以为了求得最短距离，需要从字符串两边分别遍历。先从头至尾遍历一遍数组，找到目标字母并在最终要存放的数组res的相应位置中置零；然后分别从res数组左边和右边的第二个字母开始，依次和前（后）一个字母比较，如果比前（后）一个数字大一，即把数值赋成上一个数字加一。返回最终得到的res数组。