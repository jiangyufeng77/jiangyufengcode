# 问题
作为一位web开发者， 懂得怎样去规划一个页面的尺寸是很重要的。 现给定一个具体的矩形页面面积，你的任务是设计一个长度为 L 和宽度为 W 且满足以下要求的矩形的页面。要求：

1. 你设计的矩形页面必须等于给定的目标面积。

2. 宽度 W 不应大于长度 L，换言之，要求 L >= W 。

3. 长度 L 和宽度 W 之间的差距应当尽可能小。
你需要按顺序输出你设计的页面的长度 L 和宽度 W。

# 程序
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* constructRectangle(int area, int* returnSize) {
    int i,w;
    int l = (int)sqrt(area);
    int *res = malloc(sizeof(int)*2);
    if(area == 0) 
    {
        return NULL;
    }
    for(i = l; i > 0; i--)
    {
        if(area % i == 0)
        {
            break;
        }
    }
    w = i;
    l = area / w;
    res[0] = l;
    res[1] = w;
    *returnSize = 2;
    return res;
}
```
# 心得
为了找到差值小的长和宽，可以从面积的平方根找起，取平方根的整数部分，找到可以被面积整除的值，赋值给宽w，此时长l为面积除以宽，按长和宽的顺序输出。