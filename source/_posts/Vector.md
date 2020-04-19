---
title: Vector
date: 2020-04-09 15:05:18
tags: 心得分享
---
这是我第一次写博客，请多指教！

vector是一种向量容器，说白了就是可以改变大小的数组。

vector是一个模板类，如果直接这样会报错：
```cpp
vector a; //报错，因为要指定模板。 
```
需要像这样：
<!--more-->
```cpp
vector<int> a;
       ^/*这里可以改成别的类型,float,long等等......*/
```


那么，什么是 *****模板***** 呢？

> 模板是C++支持**参数化**多态的工具，使用模板可以使用户为类或者函数声明一种一般模式，使得类中的某些数据成员或者成
员函数的参数、返回值取得任意类型。

> 　　模板是一种对**类型**进行**参数化**的工具；

> 　　通常有两种形式：**函数模板**和**类模板**；

> 　　函数模板针对仅**参数类型**不同的**函数**；

> 　　类模板针对仅**数据成员**和**成员函数类型**不同的类。

> **使用模板的目的就是能够让程序员编写与类型无关的代码。**比如编写了一个交换两个整型int

> 类型的swap函数，这个函数就只能实现**int**

> 型，对**double**，字符这些类型无法实现，要实现这些类型的交换就要重新编写另一个**swap**函数。使用模板的目的就是
要让这程序的实现与类型无关，比如一个**swap**模板函数，即可以实现**int**

> 型，又可以实现double型的交换。模板可以应用于函数和类。下面分别介绍。

> **注意：模板的声明或定义只能在全局，命名空间或类范围内进行。即不能在局部范围，函数内进行，比如不能在main函数中
声明或定义一个模板。**

**具体的请看\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\>**[点我点我!](http://www.
cnblogs.com/gw811/archive/2012/10/25/2736224.html)

```cpp

在此就不多讲了。

C++vector函数:

int size():

作用：获取vector大小。

resize(int x)

作用：变长为x。

clear()

作用：清空vector。

push_back(),pop_back():

栈操作。

 

vector                 // 创建一个空的vector。
vector c1(c2)          // 复制一个vector
vector c(n)            // 创建一个vector，含有n个数据，数据均已缺省构造产生
vector c(n, elem)      // 创建一个含有n个elem拷贝的vector
vector c(beg,end)      // 创建一个含有n个elem拷贝的vector


1. 析构函数
c.~vector ()           // 销毁所有数据，释放内存


2. 成员函数
c.assign(beg,end)c.assign(n,elem)
　　将[beg; end)区间中的数据赋值给c。将n个elem的拷贝赋值给c。
c.at(idx)
　　传回索引idx所指的数据，如果idx越界，抛出out_of_range。


c.back()      // 传回最后一个数据，不检查这个数据是否存在。
c.begin()     // 传回迭代器中的第一个数据地址。
c.capacity()  // 返回容器中数据个数。
c.clear()     // 移除容器中所有数据。
c.empty()     // 判断容器是否为空。
c.end()       // 指向迭代器中末端元素的下一个，指向一个不存在元素。
c.erase(pos)  // 删除pos位置的数据，传回下一个数据的位置。
c.erase(beg,end)  //删除[beg,end)区间的数据，传回下一个数据的位置。
c.front()     // 传回第一个数据。


get_allocator // 使用构造函数返回一个拷贝。


c.insert(pos,elem)    // 在pos位置插入一个elem拷贝，传回新数据位置。
c.insert(pos,n,elem)  // 在pos位置插入n个elem数据。无返回值。
c.insert(pos,beg,end) // 在pos位置插入在[beg,end)区间的数据。无返回值。
　　
c.max_size()       // 返回容器中最大数据的数量。
c.pop_back()       // 删除最后一个数据。
c.push_back(elem)  // 在尾部加入一个数据。
c.rbegin()         // 传回一个逆向队列的第一个数据。
c.rend()           // 传回一个逆向队列的最后一个数据的下一个位置。
c.resize(num)      // 重新指定队列的长度。
c.reserve()        // 保留适当的容量。
c.size()           // 返回容器中实际数据的个数。
c1.swap(c2)
swap(c1,c2)        // 将c1和c2元素互换。同上操作。

operator[]         // 返回容器中指定位置的一个引用。
```

**举个例子吧！**
```cpp
#include <iostream>
#include <vector>
using namespace std;


int main()
{
    vector<int> s;
    s.resize(10);            //变长为10
    s[0] = 1;
    s[1] = 2;
    s[2] = 3;
    s[3] = 4;
    s[4] = 5;
    s[5] = 6;
    s[6] = 7;
    s[7] = 8;
    s[8] = 9;
    s[9] = 10;
    cout << "vector:" << endl;
    for (auto i = s.cbegin(); i != s.cend(); i++)
        cout << *i << "  ";


    cout << "\n栈操作push_back加入18\n";
    s.push_back(18);
    for (auto i = s.cbegin(); i != s.cend(); i++)
        cout << *i << "  ";
    cout << endl;


    cout << "\n栈操作push_back加入19\n";
    s.push_back(19);
    for (auto i = s.cbegin(); i != s.cend(); i++)
        cout << *i << "  ";
    cout << endl;


    cout << "\n栈操作pop_back放走了最后的元素:\n";
    s.pop_back();
    for (auto i = s.cbegin(); i != s.cend(); i++)
        cout << *i << "  ";
    cout << endl;

    cout << "\n操作erase(s.begin+3):\n";
    s.erase(s.begin()+3);
    for (auto i = s.cbegin(); i != s.cend(); i++)
        cout << *i << "  ";
    cout << endl;
}
```

运行截图：

![](Pictures/10000201000002DA000001DE39091E0CCD706666.png)