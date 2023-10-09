# C预处理器和C库（补充语法）

## C预处理器

### 1.define()的其他语法

1.**##运算符**：预处理器粘合剂

```c
#include<stdio.h>
#deifne XNAME(n) x ## n
#define PEINT(n) printf("x" #n" = %d\n",x ## n);
int main(void)
{
    int XNAME(1) = 14;  //变成 int x1 = 14;
    int XNAME(2) = 20;   //变成int x2 = 20;
    int x3 = 30;
    PRINT(1);   // 变成printf("x1 = %d\n",x1);
    ....
}
```

`#n` 可以把记号转化成字符串；

### 2.变参宏：`...`和`__VA_ARGS__`

`#define PR(...) printf(__VA_ARGS__)`

假设稍后调用该宏：

`PR("Howay");`

`PR("weight = %d, shipping = $%.2f\n",wt,sp);`

调用后吧PR（）括号里的全部替换到printf（）里；

### 3.内联函数（C99支持）

对于简单的函数使用宏更方便；这种用法类似于定义函数。

```c
#define MAX(x,y)  ((x)>(y)?(x):(y))
#define abs(x) ((x)<0? -(x):(x))
```

c++中使用inline工具来定义内联函数。

### 4.#undef指令

#undef指令用于“取消”已经定义的#define指令。

假设有`#define x 8`这样的定义，这使用`#undef x`则可移除前面的定义。

```c
#define LIMIT 1000 			// LIMIT是已定义的
#define GOOD 				// GOOD 是已定义的
#define A(X) ((-(X))*(X)) 	// A 是已定义的
int q; 						// q 不是宏，因此是未定义的
#undef GOOD 				// GOOD 取消定义，是未定义的
```

### 其他指令函数

#### 1.#ifdef、#else和#endif指令

```c
#ifdef MAVIS
	#include "horse.h"// 如果已经用#define定义了 MAVIS，则执行下面的指令
	#define STABLES 5
#else
	#include "cow.h" //如果没有用#define定义 MAVIS，则执行下面的指令
	#define STABLES 15
#endif
////如果编译器比较旧，所写的代码就要全部靠左对齐。不支持缩进。
```

\#ifdef指令说明，如果预处理器已定义了后面的标识符（MAVIS），则 执行#else或#endif指令之前的所有指令并编译所有C代码（先出现哪个指令 就执行到哪里）。如果预处理器未定义MAVIS，且有 #else指令，则执行 #else和#endif指令之间的所有代码。

####  2.#if和#elif指令

\#if指令很像C语言中的if。#if后面跟整型常量表达式，如果表达式为非 零，则表达式为真。可以在指令中使用C的关系运算符和逻辑运算符：

```c
#if SYS == 1
#include "ibmpc.h"
#elif SYS == 2
#include "vax.h"
#elif SYS == 3
#include "mac.h"
#else
#include "general.h"
#endif
```

还有一些其他的，建议去查与C预处理器操作有关的函数。本片不再过多赘述。

## C库





