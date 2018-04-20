# 问题
 给定字符串J 代表石头中宝石的类型，和字符串 S代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。

J 中的字母不重复，J 和 S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。
# 程序
```C
int numJewelsInStones(char* J, char* S) {
    int i,j;
    int count = 0;
    for(i = 0;*(J+i) != '\0';i++)
    {
        for(j = 0;*(S+j) != '\0';j++)
        {
            if(*(J+i)==*(S+j))
            {
                count++;
            }
            else
            {
                continue;
            }
        }
        j=0;
    }
    return count;
}
```
# 心得
对两个字符串进行遍历，比较每个字符是否相同，对于相同的数，计数count加一，最终返回计数。