# 问题
给定 S 和 T 两个字符串，当它们分别被输入到空白的文本编辑器后，判断二者是否相等，并返回结果。 # 代表退格字符。
# 程序
```C
void string(char* S)
{
    int i;
    int a = 0;
    for(i = 0; S[i] != '\0'; i++)
    {
        if(S[i] != '#')
        {
            S[a++] = S[i];
        }
        else if(S[i] == '#' && a > 0)
        {
            a--;
        }
    }
    S[a] = '\0';
}
    
bool backspaceCompare(char* S, char* T) {
    string(S);
    string(T);
    if(strcmp(S,T) == 0)
    {
        return true;
    }
    else
    {
        return false;
    }
}
```
# 心得
先在一个函数中确定被输入到空白的文本编辑器后的字符串，如果字符串中的字符不是#，则将字符输入到新字符串中，否则，就后退一位，在字符串的最后加上终止符。在主函数中，将S和T字符串分别代入上个函数，得到新的字符串，然后用strcmp比较，如果相同，即strcmp返回0，则返回true，否则返回false。