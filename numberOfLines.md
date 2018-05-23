# 问题
我们要把给定的字符串 S 从左到右写到每一行上，每一行的最大宽度为100个单位，如果我们在写某个字母的时候会使这行超过了100 个单位，那么我们应该把这个字母写到下一行。我们给定了一个数组 widths ，这个数组 widths[0] 代表 'a' 需要的单位， widths[1] 代表 'b' 需要的单位，...， widths[25] 代表 'z' 需要的单位。

现在回答两个问题：至少多少行能放下S，以及最后一行使用的宽度是多少个单位？将你的答案作为长度为2的整数列表返回。
# 程序
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* numberOfLines(int* widths, int widthsSize, char* S, int* returnSize) {
    int i;
    int l = 0;
    int sum = 0;
    int* res = (int *)malloc(sizeof(int) * (*returnSize));
    for(i = 0;S[i] != '\0';i++)
    {
        l += widths[S[i] - 'a'];
        if(l > 100)
        {
            l = 0;
            sum++;
            i--;
        }
    }
    *returnSize = 2;
    res[0] = sum + 1;
    res[1] = l;
    return res;
}
```
# 心得
用for循环对S字符串中的字符逐个书写，因为26个字母所需要的单位长度在widths中设定，所以需要将每个字符和a比较得到该字母在widths中的位置，从而得到单位长度，将单位长度加起来，如果超过100，说明一行放不下，该字母要被放到第二行中，即sum加一，同时长度l置0。定义一个数组来存放结果，第一位放行数，总行数比得到的sum多一，最后一行的长度和l一样。