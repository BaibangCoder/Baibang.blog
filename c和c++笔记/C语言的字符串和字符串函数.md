# C语言的字符串和字符串函数

## 1.C语言的字符串

- char[100]="woyidingnengc";///这是一种创建方法；
- char[10]={'a','b','c','\0'};///////'\0'代表这是一个字符串；

## 2.字符串函数

### 1.strlen（）

- sizeof（）运算符是以字节为单位给出对象的大小。

- strlen（）函数给出字符串中的字符长度。**都在string.h头文件中**。

###  2.strcat

strcat()（用于拼接字符串）函数**接受两个字符串作为参数**。该函数把第 2个字符串的备份附加在第1个字符串末尾，并把拼接后形成的新字符串作为 第1个字符串，**第2个字符串不变**。strcat()函数的类型是char *（即，指向char 的指针）。strcat()函数返回第1个参数，即拼接第2个字符串后的第1个字符 串的地址。

strncat()作用和strcat一样，但接受三个参数，前俩个参数和strcat一样，第三个参数为int类型的变量，用来指定拼接到第一个字符串上的字符数量；

### 3.strcmp

字符串比较函数，接受两个指针指向字符串，从第一个字符开始比较，直到比较的不同的字符后返回一个值。strcmp()函数比较的是字符串，不是整个数组。

```c
///strcmp的返回值；
strcmp("A", "A") 返回 0
strcmp("A", "B") 返回 -1
strcmp("B", "A") 返回 1
strcmp("C", "A") 返回 1
strcmp("Z", "a") 返回 -1
strcmp("apples", "apple") 返回 1
////通过比较得：
```

大多数情况下，**strcmp()返回的具体值并不重要**，我们只在意该值是0还 是非0（即，比较的两个字符串是否相等）。或者按字母排序字符串，在这种情况下，需要知道比较的结果是为正、为负还是为0。 

**注意 ，strcmp()函数比较的是字符串，不是字符**，所以其**参数应该是字符串** （如"apples"和"A"），而不是字符（如'A'）。但是，char 类型实际上是整数 类型，所以可以使用关系运算符（>,<,=)来比较字符。

**strncmp()函数**接受三个参数，第三个参数可以指定查找的字符数。下面代码展示了是用法。

```c
#include <stdio.h>
#include <string.h>
#define LISTSIZE 6
int main()
{
    const char * list[LISTSIZE] =
    {
        "astronomy", "astounding",
        "astrophysics", "ostracize",
        "asterism", "astrophobia"
    };
    int count = 0;
    int i;
	for (i = 0; i < LISTSIZE; i++)
		if (strncmp(list[i], "astro", 5) == 0)//此处指明只比较前5个字符
        {
            printf("Found: %s\n", list[i]);
            count++;
        }
	printf("The list contained %d words beginning"
			" with astro.\n", count);
	return 0;
}
下面是该程序的输出：
Found: astronomy
Found: astrophysics
Found: astrophobia
```

### 4.strcpy

函数接受传入两个指针地址；

程序调用strcpy()把整个字符串从临时数组拷贝至目标数组中。 strcpy()函数相当于字符串赋值运算符。

strcpy()函数还有两个有用的属性。第一，strcpy()的返回类型是 char *， 该函数返回的是第 1个参数的值，即一个字符的地址。第二，第 1 个参数不 必指向数组的开始。这个属性可用于拷贝数组的一部分，即把第二个参数指向的字符串拷贝在第一个参数指向的地址，替换地址后面的字符串。

**更谨慎的选择：strncpy()**

拷贝字符串用 strncpy()更安全，该函数的第 3 个参数指明可拷贝的最大字符数，避免出现第一个字符串的空间不足以容纳第二个字符串的情况。

```c
使用strncpy时加入这两句
strncpy(qwords[i], temp, TARGSIZE - 1);
qwords[i][TARGSIZE - 1] = '\0'; 
```

这样做确保储存的是一个字符串。如果目标空间能容纳源字符串的副 本，那么从源字符串拷贝的空字符便是该副本的结尾；如果目标空间装不下 副本，则把副本最后一个元素设置为空字符。

### 其他字符串函数

ANSI C库有20多个用于处理字符串的函数，下面总结了一些常用的函数。

```c
char *strcpy(char * restrict s1, const char * restrict s2);
```

该函数把s2指向的字符串（包括空字符）拷贝至s1指向的位置，返回值是s1。

```c
char *strncpy(char * restrict s1, const char * restrict s2, size_t n);
```

该函数把s2指向的字符串拷贝至s1指向的位置，拷贝的字符数不超过 n，其返回值是s1。该函数不会拷贝空字符后面的字符，如果源字符串的字 符少于n个，目标字符串就以拷贝的空字符结尾；如果源字符串有n个或超过 n个字符，就不拷贝空字符。

```c
char *strncat(char * restrict s1, const char * restrict s2, size_t n);
```

该函数把s2字符串中的n个字符拷贝至s1字符串末尾。s2字符串的第1个 字符将覆盖s1字符串末尾的空字符。不会拷贝s2字符串中空字符和其后的字 符，并在拷贝字符的末尾添加一个空字符。该函数返回s1。

```c
int strcmp(const char * s1, const char * s2);
```

如果s1字符串在机器排序序列中位于s2字符串的后面，该函数返回一个 正数；如果两个字符串相等，则返回0；如果s1字符串在机器排序序列中位 于s2字符串的前面，则返回一个负数。

```c
int strncmp(const char * s1, const char * s2, size_t n);
```

该函数的作用和strcmp()类似，不同的是，该函数在比较n个字符后或遇 到第1个空字符时停止比较。

```c
char *strchr(const char * s, int c);
```

如果s字符串中包含c字符，该函数返回指向s字符串首位置的指针（末尾的空字符也是字符串的一部分，所以在查找范围内）；如果在字符串s中未找到c字符，该函数则返回空指针。

```c
char *strpbrk(const char * s1, const char * s2);
```

如果 s1 字符中包含 s2 字符 串中的任意字符，该函数返回指向 s1 字符串首位置的指针；如果在s1字符 串中未找到任何s2字符串中的字符，则返回空字符。

```c
char *strrchr(const char * s, int c);
```

该函数返回s字符串中c字符的最后一次 出现的位置（末尾的空字符也是字符串的一部分，所以在查找范围内）。如 果未找到c字符，则返回空指针。

```c
char *strstr(const char * s1, const char * s2);
```

该函数返回指向s1字符串中s2字符串出现的首位置。如果在s1中没有找 到s2，则返回空指针。

```c
size_t strlen(const char * s);
```

该函数返回s字符串中的字符数，不包括末尾的空字符。

```c
char *strcpy(char * restrict s1, const char * restrict s2);
///有const不会改变字符串
```

表明不能更改s2指向的字符串，至少不能在strcpy()函数中更改。但是可 以更改s1指向的字符串。这样做很合理，因为s1是目标字符串，要改变，而 s2是源字符串，不能更改。

目前总结出这么多，日后有改动再补充；

