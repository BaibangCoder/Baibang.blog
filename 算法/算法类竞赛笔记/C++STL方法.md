[TOC]

# 字符串string

字符串string需要使用头文件`<string>`。包含下面语法：

1. `string s`：定义一个名字为s的字符串字面量。
2. `s+=str`或`s.append(str)`:在字符串s**后面**拼接字符串str。
3. `s<str`：比较字符串s的字典序是否在字符串str的字典序之前。
4. `s.size()`或`s.length()`：得到字符串s的长度。
5. `s.substr(pos,len)`：截取字符串s，从第pos个位置开始len个字符，并返回这个字符串。
6. `s.insert(pos,str)`:在字符串s的第pos个字符==之前==插入字符串str，并返回这个字符串。
7. `s.find(str,pos)`：在字符串s中从第pos个字符开始寻找str，并返回位置，如果找不到返回-1。pos可以省略，默认值为0。

# 栈

栈的头文件是`<stack>`，有以下几种方法：

1. `stack<int>s`:建立一个栈s，其内部元素类型为int；
2. `s.push(a)`：将元素a压进栈s；
3. `s.pop()`：将s的栈顶元素弹出；
4. `s.top()`：查询s的栈顶元素；
5. `s.size()`：查询s的元素个数；
6. `s.empty()`：查询s是否为空。

# 普通队列

队列的头文件是`<queue>`，有以下几种方法：

1. `queue<int>q`：建立一个队列q，其内部元素类型为int；
2. `q.push(a)`：将元素a插入到队列q的末尾；
3. `q.pop()`：删除队列q的队首元素；
4. `q.front()`：查询q的队首元素；
5. `q.back()`：查询q的队尾元素；
6. `q.size()`：查询q的元素个数；
7. `q.empty()`：查询q是否为空；

# 双端队列deque

双端队列可以在队头和队尾插入和删除元素，也仅能在队头和队尾删除和插入

包含头文件deque

1. `dq[i]`：返回队列中下标为i的元素
2. `dq.front()`：返回队头
3. `dq.back()`：返回队尾
4. `dq.pop_back()`：删除队尾，不返回值
5. `dp.pop_front()`：删除队头，不返回值
6. `dp.push_back(e)`：在队尾添加一个元素e
7. `dp.push_front(e)`：在队头添加一个元素e

# priority_queue(优先队列STL)

接受三个参数（第一个参数是存储对象的类型，第二个参数是存储元素的底层容器，第三个参数是函数对象）

例如：`priority_queue(int , vector<int> , greater<int>);`// 此时创建的是一个小根堆

```C++
// 常用的优先队列
priority_queue <node> q;
//node是一个结构体
//结构体里重载了‘<’小于符号
priority_queue <int,vector<int>,greater<int> > q;
//不需要#include<vector>头文件
//注意后面两个“>”不要写在一起，“>>”是右移运算符
priority_queue <int,vector<int>,less<int> >q;

```

默认是从大到小排列

对 `priority_queue` 进行操作有一些限制：

- `push(const T& obj)`：将obj的副本放到容器的适当位置，这通常会包含一个排序操作。
- `push(T&& obj)`：将obj放到容器的适当位置，这通常会包含一个排序操作。
- `emplace(T constructor a rgs...)`：通过调用传入参数的构造函数，在序列的适当位置构造一个T对象。为了维持优先顺序，通常需要一个排序操作。
- `top()`：返回优先级队列中第一个元素的引用。
- `pop()`：移除第一个元素。
- `size()`：返回队列中元素的个数。
- `empty()`：如果队列为空的话，返回true。
- `swap(priority_queue<T>& other)`：和参数的元素进行交换，所包含对象的类型必须相同。

# lower_bound()和upper_bound()

思想就是二分，可以使用二分法来写

在离散化中可以使用

使用前提：：只是简单的查找x和x附近的数

```C++
upper_bound()// 查找第1个大于x的元素位置
bin_search()// 和lower_bound()的功能一致
lower_bound()// 查找第一个等于或大于x的位置
```



# fill()

当我们想对一个容器的值进行填充时，我们就可以使用fill()函数。

## 使用fill()函数填充普通一维数组

```C++
  fill (array,array+4,5);   // myvector: 5 5 5 5 0 0 0 0
  fill (array+3,array+6,8);   // myvector: 5 5 5 8 8 8 0 0
```

在使用数组 array 时，array代表的就是array[]的起始地址，而array+4代表的就是在起始向后偏移4个位置的元素。 所以：fill (array,array+4,5); 得到的结果就是array[0] = array[1] = array[2] = array[3] = 5。后面的操作同理，不再叙述。
## 使用fill()函数填充vector

```C++
fill (myvector.begin(),myvector.begin()+4,5);   // myvector: 5 5 5 5 0 0 0 0
fill (myvector.begin()+3,myvector.end()-2,8);   // myvector: 5 5 5 8 8 8 0 0
```

因为vector不再是普通的数组了（即使它可以被视作是一个数组），所以我们不需要使用数组首地址的方式，因为vector已经给我们封装好了方法，其初始地址就是vector.begin()，末位地址就是vector.end()。其余同array。
## 使用fill()函数填充二维数组

简要代码：

```C++
fill(G[0],G[0]+6*4,520);
// 填充6行4列的数值为520
```




# memset（初始化函数）

函数接受三个参数，第一个参数为数组的地址，第二个参数为初始化值，第三个参数为数组的大小，按字节计算（用sizeof提取）；

例如`int s[10];  memset(s,0,sizeof(s));`表示把s数组里的10个元素都初始化为0,使用sizeof（）自动计算初始化的字节数；

在这个例子中第二个参数**为0是，初始化为0**；**为127时初始化为int的极大值**；**为128时初始化为一个极小值**；**为-1或255时初始化为-1**；



# map  关联容器

参考链接：[C++ STL map容器详解 (biancheng.net)](http://c.biancheng.net/view/7173.html)

map翻译为映射，也是常用的STL容器，单次查找的时间接近O(logn)；	底层使用平衡的搜索树——**红黑树**实现

map可以==将任何基本类型（包含STL容器）映射到任何基本类型（包含STL容器）==，也就可以建立string型到int型的映射。
		如果要使用map,需要添加map头文件，即`#include<map>`。除此之外，还需要在头文件下面加上一句：“`using namespace std;`”,这样就可以在代码中使用map了。

2.map的定义：单独定义一个map:

`map<key,value> mp;`

map 和其他STL容器在定义上有点不一样，因为map**需要确定映射前的类型（键 key）和映射后类型（值 value）**,所以需要在<>内填写两个类型，其中**第一个是键的类型，第二个是值的类型**。如果是int 型映射到 int 型，就相当于是普通int 型数组。

map容器会根据**key值**自动排序，**升序**排序；

而如果是**字符串到整型的映射，必须使用 string 而不能用 char 数组**：**

`map<string,int> mp;`

这是因为 char 数组作为数组，是不能被作为键值的。如果想用字符串作映射，必须用 string 。

```c++
  // 另外同vector容器一样，map的键和值也可以是STL容器，例如可以将一个set容器映射到一个字符串；
```

`map<set<int>,string> mp;`

3.map容器内元素的访问
  map一般用两种访问方式：通过**下标**访问或通过**迭代器**访问。

4.map的访问方式：
（1）通过下标访问：  直接使用 **mp ['c']** 的方式来访问它对应的整数，key值就是下标。  需要注意的是，同 set 容器相同，**map 中的键是唯一的**。

（2）通过迭代器访问：和其他迭代器的定义方式相同：

​	`map<typename1,typename2>:: iterator it;`      使用方法和指针类似

​	(3) 访问方式map可以使用 `it->first` 来访问键，使用 `it->second` 来访问值。

​	进行遍历时，全遍历的范围时`for(it=mp.begin ; it!=mp.end() ; it++)`

​	嵌套的map可以使用，前面的`it->second.begin()`表示第一个位置，其他类似

```c++
//样例代码
#include<cstdio>
#include<cstring>
#include<iostream>	
#include<algorithm>
using namespace std;
#include<map>////需要包含map头文件才可以使用map容器
int main()
{
	map<char,int> mp;////char字符映射到int类型//可以是任意类型映射到任意类型
	mp['c']=20;	mp['c']=30;	mp['m']=20;	mp['r']=30;	mp['a']=40;//映射//如果有重复，则会覆盖映射
    ///int a,b;		mp[a]=b;//如果有重复，则覆盖
    //	mp.insert(pair<int,int>(a,b));//使用pair合并，然后插入，能自动排序，如果有重复，则忽略，不会覆盖
	for(map<char,int>::iterator it=mp.begin();it!=mp.end();it++)    //运用迭代器依次输出 ！！ map会以键从小到大的顺序自动排序 
	{
		cout<<it->first<<" "<<it->second<<endl;////需要使用->来输出，第一个为first,第二个为second
	}
    //for(auto it:map){//直接利用auto推断it迭代器的类型，自动排序输出
    //	cout<<it->first<<" "<<it->second<<endl;///
	//}
	cout<<mp.size()<<endl; 
	map<char,int>::iterator tt=mp.find('a');
	cout<<tt->first<<" "<<tt->second<<endl;	//运用迭代器单个指定输出 
	//mp.erase(tt);//单个删除 
	mp.erase('c');//另一种单个删除 
	mp.erase(it,mp.end());//进行区间删除 
	cout<<mp.size()<<endl;//输出删除后的区间长度 
	mp.clear();
	cout<<mp.size()<<endl;
	//cout<<mp['c']<<endl;//输出 mp['c'];
	return 0;
}
```



嵌套map直接当二维数组来输入输出即可；

`map<int,map<int>>mp;`

## unordered_map

本质上是hash算法，单次查找的时间复杂度可以接近O(1)；

输入的值不会排序，使用查找时间快；

用法和普通map比较类似

# set

定义于`<set>`头文件中，位于std空间中；底层使用平衡的搜索树——==红黑树==实现

set，顾名思义是“集合”的意思，在set中==元素都是唯一==的；**可以根据这一特性实现数组去重**

set只允许一个值出现一次，如果需要集合中的元素允许**重复**那么可以使用**multiset**。

操作时需要依靠迭代器，指针来操作，不涉及内存拷贝和移动，所以效率高；输入数据后与map一样，**自动根据key值升序排序**；

`set<string>nams;`就定义了一个string类型的set，叫nams；

`set<string>copyst(nams);`会创建一个string类型的set，叫copyst，并且把nams中的元素复制一份到copyst

set容器的创建

```c++
#include <iostream>
#include <set>
#include <functional>
using namespace std;
	set<int> s;
//////////////////////////////////////////////////////////////////////////////////////////////////////
   set<int > seta; //默认是小于比较器  less<int>  的set
   set<int, greater<int> > setb; //创建一个带大于比较器的set，需包含头文件functional
   int a[5] = {1,2,3,4,5};
   set<int > setc(a,a+5); //使用数组a初始化一个set；//可以进行区间插入，指定插入几个元素
   set<int > setd(setc.begin(),setc.end()); //setc初始化一个set
   //上述两例均为区间初始化
   set<int > sete(setd); //拷贝构造创建set//此时sete中的元素和setd一样
```

set容器的操作

```c++
#include<set>
using namespace std;
s.begin()//返回set容器的第一个元素
s.end()//返回set容器的最后一个元素
s.clear()//删除set容器中的所有的元素
s.empty()//判断set容器是否为空	
s.insert()//插入一个元素	//只有一个参数，要插入哪个元素，写哪个元素
s.erase()//删除一个元素	//只有一个参数，写要删除的元素
s.size()//返回当前set容器中的元素个数
    //不能直接修改容器里的元素，只能先删除，再插入修改后的值
s.find()        //查找一个元素，如果容器中不存在该元素，返回值等于s.end()
    //使用set<int>::iterator pos = s.find(3);，查找元素1的时间复杂度为O(logN)//因为set的底层是搜索树;
    //使用set<int>::iterator pos = find(s.begin(), s.end(), 3);的时间复杂度为O(N),//注意是三个参数;

set::count()//是C++ STL中的内置函数，它**返回元素在集合中出现的次数**。由于set容器仅包含唯一元素，因此只能返回1或0。
//用法：set_name.count(element)
//参数：该函数接受一个强制性参数element，该元素指定要返回其计数的元素。
//返回值：该函数返回1或0，因为该集合仅包含唯一元素。如果设置的容器中存在该值，则返回1。如果容器中不存在它，则返回0。
```

其他常用操作

```c++
s.lower_bound() //	返回第一个大于或等于给定关键值的元素

s.upper_bound() //	返回第一个大于给定关键值的元素

s.equal_range() //	返回一对定位器，分别表示 第一个大于或等于给定关键值的元素 和 第一个大于给定关键值
                //	的元素，这个返回值是一个pair类型，如果这一对定位器中哪个返回失败，就会等于
                //	s.end()
```

## multiset

允许容器里有重复的元素

# List

```C++
	list<int> l			声明一个空链表
	list<int> l{1,2,3}	声明一个含指定元素的链表
	list<int> l(n)    	声明一个含n个元素的链表并全部初始化为0
	list<int> l(n, m)  	声明一个含n个元素的链表并全部初始化为m
	list<int> l(a,b)  	声明一个链表并初始化为区间[a,b]中的元素，a、b是迭代器

```

#### 基本操作

```C++
增：
	l.insert() 					插入一个元素到list中
	l.push_back() 				在list的末尾添加一个元素 
	l.push_front() 				在list的头部添加一个元素
	
删：
	l.clear() 					清空list的所有元素
	l.erase() 					删除一个元素
	l.erase(l.begin(),l.end())  将l从begin()到end()之间的元素删除。
	l.pop_back() 				删除最后一个元素 
	l.pop_front() 				删除第一个元素
	l.remove() 					从list删除指定元素 
	l.remove_if() 				按指定条件删除元素
	l.unique() 					删除list中重复的元素
	
改：
	l.resize() 					改变list的大小
	l.reverse() 				把list的元素倒转
	
查：
	l.front() 					返回第一个元素 
	l.back() 					返回最后一个元素
	l.empty() 					若list是空的则返回true，否则返回false
	l.max_size() 				返回list能容纳的最大元素数量 
	l.size() 					返回list中的元素个数

其他操作：
	l.assign() 					给list赋值
	l.get_allocator() 			返回list的配置器
	l.merge() 					合并两个list
	l.begin() 					返回指向第一个元素的迭代器 
	l.end() 					返回末尾的迭代器
	l.rbegin() 					返回指向第一个元素的逆向迭代器 
	l.rend() 					指向list末尾的逆向迭代器
	l.sort() 					给list排序
	l.splice() 					合并两个list
	l.swap() 					交换两个list

```



# vector

使用时需要包含`#include<vector>`头文件

vector是一个向量容器，使用方法和二维数组差不多，可以当个变长数组使用

1. ```c++
   ///创建并初始化一个vector
   vector<int> a(10); //定义了10个整型元素的向量（尖括号中为元素类型名，它可以是任何合法的数据类型），但没有给出初值，其值是不确定的。
   vector<int> a(10,1); //定义了10个整型元素的向量,且给出每个元素的初值为1
   vector<int> a(b); //用b向量来创建a向量，整体复制性赋值//b为下面的数组
   vector<int> a(b.begin(),b.begin+3); //定义了a值为b中第0个到第2个（共3个）元素
   int b[7]={1,2,3,4,5,9,8};
           vector<int> a(b,b+7); //从数组中获得初值
   ```

2. ```c++
   （1）a.assign(b.begin(), b.begin()+3); //b为向量，将b的0~2个元素构成的向量赋给a
   （2）a.assign(4,2); //是a只含4个元素，且每个元素为2
   （3）a.back(); //返回a的最后一个元素
   （4）a.front(); //返回a的第一个元素
   （5）a[i]; //返回a的第i个元素，当且仅当a[i]存在2013-12-07
   （6）a.clear(); //清空a中的元素
   （7）a.empty(); //判断a是否为空，空则返回ture,不空则返回false
   （8）a.pop_back(); //删除a向量的最后一个元素
   （9）a.erase(a.begin()+1,a.begin()+3); //删除a中第1个（从第0个算起）到第2个元素，也就是说删除的元素从a.begin()+1算起（包括它）一直到a.begin()+         3（不包括它）
   （10）a.push_back(5); //在a的最后一个向量后插入一个元素，其值为5
   （11）a.insert(a.begin()+1,5); //在a的第1个元素（从第0个算起）的位置插入数值5，如a为1,2,3,4，插入元素后为1,5,2,3,4
   （12）a.insert(a.begin()+1,3,5); //在a的第1个元素（从第0个算起）的位置插入3个数，其值都为5
   （13）a.insert(a.begin()+1,b+3,b+6); //b为数组，在a的第1个元素（从第0个算起）的位置插入b的第3个元素到第5个元素（不包括b+6），如b为1,2,3,4,5,9,8         ，插入元素后为1,4,5,9,2,3,4,5,9,8
   （14）a.size(); //返回a中元素的个数；
   （15）a.capacity(); //返回a在内存中总共可以容纳的元素个数
   （16）a.resize(10); //将a的现有元素个数调至10个，多则删，少则补，其值随机
   （17）a.resize(10,2); //将a的现有元素个数调至10个，多则删，少则补，其值为2
   （18）a.reserve(100); //将a的容量（capacity）扩充至100，也就是说现在测试a.capacity();的时候返回值是100.这种操作只有在需要给a添加大量数据的时候才显得有意义，因为这将避免内存多次容量扩充操作（当a的容量不足时电脑会自动扩容，当然这必然降低性能） 
   （19）a.swap(b); //b为向量，将a中的元素和b中的元素进行整体性交换
   （20）a==b; //b为向量，向量的比较操作还有!=,>=,<=,>,<
   ```

# array

| 成员函数            | 功能                                                         |
| ------------------- | ------------------------------------------------------------ |
| begin()             | 返回指向容器中第一个元素的随机访问迭代器。                   |
| end()               | 返回指向容器最后一个元素之后一个位置的随机访问迭代器，通常和 begin() 结合使用。 |
| rbegin()            | 返回指向最后一个元素的随机访问迭代器。                       |
| rend()              | 返回指向第一个元素之前一个位置的随机访问迭代器。             |
| cbegin()            | 和 begin() 功能相同，只不过在其基础上增加了 const 属性，不能用于修改元素。 |
| cend()              | 和 end() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。 |
| crbegin()           | 和 rbegin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。 |
| crend()             | 和 rend() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。 |
| size()              | 返回容器中当前元素的数量，其值始终等于初始化 array 类的第二个模板参数 N。 |
| max_size()          | 返回容器可容纳元素的最大数量，其值始终等于初始化 array 类的第二个模板参数 N。 |
| empty()             | 判断容器是否为空，和通过 size()==0 的判断条件功能相同，但其效率可能更快。 |
| at(n)               | 返回容器中 n 位置处元素的引用，该函数自动检查 n 是否在有效的范围内，如果不是则抛出 out_of_range 异常。 |
| front()             | 返回容器中第一个元素的直接引用，该函数不适用于空的 array 容器。 |
| back()              | 返回容器中最后一个元素的直接应用，该函数同样不适用于空的 array 容器。 |
| data()              | 返回一个指向容器首个元素的[指针](http://c.biancheng.net/c/80/)。利用该指针，可实现复制容器中所有元素等类似功能。 |
| fill(val)           | 将 val 这个值赋值给容器中的每个元素。                        |
| array1.swap(array2) | 交换 array1 和 array2 容器中的所有元素，但前提是它们具有相同的长度和类型。 |





# 二叉堆（priority_queue）

` priotity_queue<int,vector<int>,greater<int>>q;`定义一个堆

`q.push()`压入一个元素

`q.top`取内最小元素

`q.pop()`删除堆内最小的数

# 排列next_permutation()

这是一个求“下一个”全排列的函数。函数**返回bool值**，如果没有下一个排列组合，返回false，否则返回true。每执行函数一次，会把新的排列放到原来的空间里。

注意：如果要得到所有的全排列，需要从最小的全排列开始。如果初始不是最小的，需要使用sort（）函数排序。

==**还有一个全排列函数**==:`prev_permutation`；即求“前一个”排列组合，与上面的函数相反，即从大到小排列。



# 函数合集

## 字符串函数

- isalpha()用来判断一个字符是否为字母
- isalnum用来判断一个字符是否为数字或者字母，也就是说判断一个字符是否属于a~ z||A~ Z||0~9。
- isdigit() 用来检测一个字符是否是十进制数字0-9
- islower()用来判断一个字符是否为小写字母，也就是是否属于a~z。
- isupper()和islower相反，用来判断一个字符是否为大写字母。













>
>
>
