# C++基础学习笔记





## 引用

​	引用就是给变量创建别名

​	引用必须初始化，且初始化后不允许改变

```C++
// 例如
int a = 20;
int &b = a;//使用&符号来创建引用变量
// 此时a和b指向同一块内存
```

 ### 使用引用做函数参数

由于在函数中修改实参之前只能使用指针来修改，现在可以用引用来修改，更好用；

**使用方法和直接使用变量名称没有差别**

### 引用做函数返回值

// 1、不要返回局部变量的引用，局部变量存放在栈区，运行过去就消失了

// 2、函数的调用可以作为左值

### 引用的本质

本质：在C++内部实现的一个指针常量；



