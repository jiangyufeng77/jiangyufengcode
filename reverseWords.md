# 问题
给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。

# 程序
```C
char* reverseWords(char* s) {
    char *start = s;
    char *end = s;
    char *p = s;
   
    while(*p != '\0')
    {
        while (*end != ' ' && *end != '\0')
        {
            end++;
        }
        p = end;
        end--;
        
        while (start < end)
        {
            char t;
            t = *start;
            *start++ = *end;
            *end-- = t;
        }
        if (*p != '\0')
        {
            p++;
            start = p;
            end = p;
        }
    }
    
    return s;
}
```
# 心得
因为是要对每个单词反转，而不是整个一句话，所以需要逐个单词遍历反转。用到三个指针，分别指向字符串，p用来检测是否是一个单词，以空格或空字符为界，对于一个单词进行反转，反转完成后，再开始进入下个单词，直到整个字符串结束。