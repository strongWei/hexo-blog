---
title: JavaScript 基础篇 - 函数
categories:
  - JavaScript
tags:
---
JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。
 
### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)>并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的>知识点总结 
 
<!-- more -->

#### 函数的定义
主要有三种方式，如下:  
```js
//普通定义
function func1(){
}

//函数表达式
var a = function(){};

//构造法，最后一个参数表示函数体，其它的表示函数的参数
var a = new Function(
	'x',
	'y',
	'return x + y'
);   
```
这里主要重点讲一下函数表达式，它相当于一个匿名的函数，可以带有函数名，但函数名只能在函数体内有效。  
添加函数名有两个好处，第一是可以在函数体内部调用自己，第二个是方便除错，主要用于调试。

#### 函数的重复声明
后面的声明会覆盖前面的，这个与函数名的提升有关。

#### 函数名的提升
与变量名的提升是一样的  
由此可得出推论，*如果同时采用`function`和函数表达式声明同一个函数，最后总是采用函数表达式*


#### name属性
如果是普通的定义，直接返回函数名，如果函数表达式定义的函数有名字，则返回这个名字，反之返回变量名。  
特殊的用法: 使用函数表达式f，可以在调用f的函数内部获取函数的名字，方便知道传入的函数是什么函数。

#### length属性
用于获取函数预期传入的参数个数，而不是调用时的参数个数。

#### toString属性
用于返回函数的源码

#### 作用域
作用域需要注意:  
- 在ES6之前，局部的作用域只在函数中才出现
- 函数内部也存在变量提升
- 函数执行时所在的作用域，是定义的作用域，而不是调用时所在的作用域
	- 函数B在函数A外部定义，函数A调用函数B, B不能引用函数A定义的变量 
	- 函数体内部声明的函数，作用域绑定函数体内部，这促成了闭包的出现
- 如果在函数内部不使用`var`, 定义的变量将会在函数执行后变成全局变量

```js
var a = 1;
var x = function () {
  console.log(a);
};

function f() {
  var a = 2;
  x();
}

f() // 1
``` 

#### 参数
参数可