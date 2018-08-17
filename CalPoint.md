# 问题
你现在是棒球比赛记录员。
给定一个字符串列表，每个字符串可以是以下四种类型之一：
1.整数（一轮的得分）：直接表示您在本轮中获得的积分数。
2. "+"（一轮的得分）：表示本轮获得的得分是前两轮有效 回合得分的总和。
3. "D"（一轮的得分）：表示本轮获得的得分是前一轮有效 回合得分的两倍。
4. "C"（一个操作，这不是一个回合的分数）：表示您获得的最后一个有效 回合的分数是无效的，应该被移除。

每一轮的操作都是永久性的，可能会对前一轮和后一轮产生影响。
你需要返回你在所有回合中得分的总和。
# 程序
```C
int calPoints(char** ops, int opsSize) {
    int i;
    int k = 0;
    int sum = 0, num = 0;
    int *valid = (int*)malloc(sizeof(int)*opsSize);
    for(i = 0;i < opsSize;i++)
    {
        if(*ops[i] == '+')
        {
            num = valid[k-2] + valid[k-1];
            valid[k] = num;
            k++;
            sum += num;
        }
        else if(*ops[i] == 'D')
        {
            num = valid[k-1] * 2;
            valid[k] = num;
            k++;
            sum += num;
        }
        else if(*ops[i] == 'C')
        {
            sum -= valid[k-1];
            valid[k] = 0;
            k--;
        }
        else
        {
            num = atoi(ops[i]);
            sum += num;
            valid[k] = num;
            k++;
        }
    }
    return sum;
}
```
# 心得
根据题意，将循环分为4种情况，设定一个新的有效数组valid。atoi函数代表的意思是将字符串转换成整数int，如果输入的是整数，则总数就等于整数，valid数组也在相应位置存放整数；如果输入的是D，则将valid数组中上一个数乘2；如果输入的是+，则将valid数组中上两个数的和计入总数；如果输入的是C，则将上一个数减去。最终返回总数sum。
