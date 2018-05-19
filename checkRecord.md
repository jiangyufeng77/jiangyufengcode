# 问题

给定一个字符串来代表一个学生的出勤纪录，这个纪录仅包含以下三个字符：

'A' : Absent，缺勤
'L' : Late，迟到
'P' : Present，到场
如果一个学生的出勤纪录中不超过一个'A'(缺勤)并且不超过两个连续的'L'(迟到),那么这个学生会被奖赏。

你需要根据这个学生的出勤纪录判断他是否会被奖赏。
# 程序
```C
bool checkRecord(char* s) {
    int countA = 0, countL = 0;
    while(*s != '\0')
    {
        if(*s == 'A')
        {
            countA++;
            countL = 0;
            if(countA > 1)
            {
                return false;
            }
        }
        else if(*s == 'L')
        {
            countL++;
            if(countL > 2)
            {
                return false;
            }
        }
        else
        {
            countL = 0;
        }
        s++;
    }
    return true;
}
```
# 心得
定义两个变量来存放字母A和L的次数，依次检查字符串中的字母，如果是A，代表缺勤，计数A加一，根据题意，如果计数A比一大，就false，同时因为迟到得是连续的两个L，如果检测到了别的字母，就令计数L置零；检测到字母L时，计数L加一，当它比二大时，就false；如果上述两种情况都没出现，就返回true。