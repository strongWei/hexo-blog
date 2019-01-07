---
title: 数据结构基础篇 - C++ 
tags:
- cpp
categories:
- Computer
---
数据结构是计算机基础中的重要组成部分，虽然现代计算机语言很多都很少使用到数据结构，对于数据结构的底层实现也不是那么重视，但是我认为数据结构仍然是必须掌握的。

本系列是通过 **数据结构与算法分析（C++描述）** 这本书的学习来进行知识的归纳和总结，它同样不是完整的学习教程，只是为了记忆在此记录而已。  

本篇主要是讲述C++的一些基础，为后面数据结构的实现打下基础。

<!-- more -->

### Knowledge  
 
#### C++ 细节
> 这里并没有系统的讲述C++类的所有知识，只是对一些比较重要的细节进行阐述。

##### 初始化列表  
- **const成员变量** 只能在此初此化
- **数据成员是不具有零参数的构造函数的类类型** 只能在此初始化

##### explicit
该标志符只用在单参数的构造函数上，它的使用是为了防止类实例在初始化时进行**隐式类型转换**，如:
```c++
Test test(0);

//这里将会发生隐式类型转换
Test k;
k = 1;
```

##### 常量成员函数
防止在定义的函数内对类的成员变量进行修改。
```c++
class A{
    int read() const;
}
```

##### 数组的局限性
1. `=` 不能用来复制
2. 不能获取数组的长度

##### 三种参数传递机制
包括常量引址传递，引址传递，按值传递。  

选用依据:  
a. 传递的参数希望被改变，应使用`引址传递`  
b. 传递的参数不希望被改变，如果是简单类型，应该使用`按值传递`，如果传递的是类类型，一般使用 `常量引址传递`

>返回值传递机制也包括上述三种机制，其中，使用引用传参时比较容易出错的情况是返回的是函数创建的局部变量。

##### 复制构造函数
调用的时机  
a. 声明的同时初始化
```c++
Test a = b;
Test a(b);
```
b. 使用按值调用传递对象  
c. 使用按值调用返回对象

浅复制与深复制  
当对象的成员在复制时仅仅是复制成员的地址时，就叫做浅复制; 否则就叫做深复制。这种情况仅限于对象成员是指针或类类型。


实践：深复制必须定义析构函数，复制构造函数和 operator`=`
***带指针的成员变量***
```c++
class IntCell{
    public:
        explicit InCell(int value){
            storeValue = new int(value);
        }
        ~IntCell(){
            delete storeValue;
        }
        IntCell(const IntCell &ini){
            storeValue = new int(*ini.storeValue);
        }
        const IntCell& operator=(const IntCell& ini){
            if(this != &ini){
                *storeValue = *ini.storeValue;
            }
            return *this;
        }

    private:
        int* storeValue;
}
```

##### 函数模板
函数模板并不是函数，而是用于生成函数代码。它可以不同的参数类型来生成不同的代码。
```c++
template <typename Comparable>
const Comparable & findMax( const Vector<Comparable>& a){
    int maxIndex = 0;
    for (int i=0; i < a.size(); ++i){
        if(a[i] > a[maxIndex]){
            maxIndex = i;
        }
    }
    return a[maxIndex];
}
```

##### 类模板
```c++
templae <typename Object>
class MemoryCell{
    public:
        explicit MemoryCell(const Object& initial = Object()):storeValue(initial){}
        const Object &read() const { return storeValue;}
        void write(Object& obj){
            storeValue = obj;
        }
    private:
        Object storeValue;
}
```

##### 函数对象
出现的原因: 有时候函数模板要求传入的类对象必须实现特定的操作符重载才能使用，为了避免这种情况应运而生

```c++
template <typename Object, type Comparable>
const Object & findMax(const vector<Object> & arr, Comparable comp){
    int maxIndex = 0;
    for (int i=0;i<arr.size();++i){
        if(comp.isLessThan(arr[maxIndex], arr[i])){
            maxIndex = i;
        }
    }

    return maxIndex;
}


class CaseInsentiveCompare
{
    public:
        bool isLessThan(const string& lhs, const string& rhs) const
        {
            return stricmp(lhs.c_str(), rhs.c_str()) < 0;
        }
}

int main(int argc, char** argv){
    findMax(arr, CaseInsentiveCompare()));
}
```

使用标准库函数生成一个对象模板

##### ~~矩阵~~

### Exprience
1. 如果你有在构造函数中 `new` 成员变量，那么就必须在析构函数中 `delete`。
