```c
#include<stdio.h>
#include<string.h>
////
////
////
////
char* s_gets(char* st, int n)
{
    char* ret_val;
    int i=0;
    //fgets函数返回读取的第一个字符的地址
    ret_val = fgets(st,n,stdin);
    if(ret_val)
    {
        while(st[i] != '\n'&& st[i]!='\0')
            i++;
        /*  由于fgets函数的特性，此时最多读入了n-1个字符
            如果有多余输入，还存在输入流中*/
        if(st[i]=='\n')
            st[i]='\0';
        else while(getchar()!='\n')//将多余字符丢掉
            continue;
    }
    return ret_val;
}
```

