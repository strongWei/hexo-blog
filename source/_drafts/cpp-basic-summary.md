---
title: C++基础篇 - 应用总结
tags:
categories:
  - cpp
---
本系列是通过 **C++程序设计语言 原书第四版** 这本书的学习来进行知识的归纳和总结，它同样不是完整的学习教程，只是为了记忆在此记录而已。  

本篇主要是讲述c++的一些基础用法，经过之前的经验，对一些未知的或者新的知识进行总结。

<!-- more -->

### Knowledge
#### 变量的初始化符 `{}`
作用与`=`的用法类似，不同在于它不会进行隐式转换。
```c++
int k{1.2}; //error:
```

#### auto的作用
系统根据初始化值自动判断类型。 还要再看看。


#### 算法分析
平均情形和最坏情形

分析的法则
四个法则

举例分析递归算法斐波那契数列
