# 问题
给定一个赎金信 (ransom) 字符串和一个杂志(magazine)字符串，判断第一个字符串ransom能不能由第二个字符串magazines里面的字符构成。如果可以构成，返回 true ；否则返回 false。

(题目说明：为了不暴露赎金信字迹，要从杂志上搜索各个需要的字母，组成单词来表达意思。)

注意：

你可以假设两个字符串均只含有小写字母。
# 程序
```C
bool canConstruct(char* ransomNote, char* magazine) {
    int i;
    int l1 = strlen(ransomNote);
    int l2 = strlen(magazine);
    int count[128] = {0};
    for(i = 0; i < l1; i++)
    {
        count[ransomNote[i]]++;
    }
    for(i = 0; i < l2; i++)
    {
        count[magazine[i]]--;
    }
    for(i = 0; i < 128; i++)
    {
        if(count[i] > 0)
        {
            return false;
        }
    }
    return true;
}
```
# 心得
新设定一个数组，因为大写字母和小写字母的ASCII码最高为122，可以设定count长度为128。分别对ransomNote和magazine数组循环，ransomNote数组中的每个字母在count数组中对应地方加一，magazine减一，如果有不包含的，则count数组中的数会大于0，此时返回false，否则true。