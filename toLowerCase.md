# 问题
实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。

# 程序
```C
char* toLowerCase(char* str) {
    if(*str == NULL) 
        return NULL;
	char *t = str;
	while(*str != '\0')
    {
		if(isalpha(*str) && !islower(*str)) 
        {
            *str = *str + 32; 
        }  
		str++;
	}
	str = t;
	return str;
}
```
# 心得
如果字符串长度为0，则返回NULL。否则设一个新的指针t,使其和从str的第一个字母开始移动，如果是该字符是英文字母，且是非小写字母，就将其加32（根据ASCII码），转换成小写字母，指针后移，直到全部改完，返回str。