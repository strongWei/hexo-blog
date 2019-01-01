---
title: JavaScript 基础 - 语法篇
categoryes:
  - JavaScript
date: 2018-12-29 08:31:46
tags:
---

JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。

### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的知识点总结  

<!-- more -->

#### 重声明变量  
重新声明一个已经存在的变量，如果新声明的变量没有赋值，则声明无效，如果有赋值，则将会覆盖之前的变量 

#### 变量提升  
何为变量提升？看下面代码就明白了  
```js
console.log(a); //输出 undefined
var a = 2;

//上面的代码不会报错: 未定义
//它相当于:
var a;
console.log(a);
a = 2; 
```

#### 命名规则  
- 首字符必须是unicode字母（英文字母或其它语言的字母）、_、$
- 次字符及之后的字符除了可以用上面的规则之外，还可以使用0-9  
>由此可见，中文也可以作为变量
  
**三种注释**
看下面代码就明白了
```js
//comment

/*
 comment
*/

var k=2; <!-- comment

--> 这里必须自成一行	
var k = 20;
```

**switch比较运算规则**  
使用的是严格的 `===`，因此不能通过类型自动转换机制

**Label**  
1. 与`break`和`continue`配合使用，看下面代码
注意：使用 `continue` 时 Top不能是代码块，否则会报错
```js
Top:
	for(var i=0;i<3;++i){
		for(var j=0;j<2;++j){
			if(i==1 && j==1){
				break Top; //continue Top;
			}
			console.log('i=' + i + ',j=' + 'j'); 
		}	
	}

//当使用break时, 当满足条件时，将会马上跳到Top标签的下面，输出结果如下:
//这里实际上也是跳出代码块
//i=0,j=0 i=0,j=1 i=1,j=0 
 
//当使用continue时，当满足条件时，将会跳到最外层的for上，
//i=0,j=0 i=0,j=1 i=1,j=0 i=2,j=0 ...
```
2. 跳出代码块，看下面代码  
注意: 不能使用`continue`跳出，否则会报错
```js
Top:{
	var k=2;
	console.log(k);
	break Top;
	console.log(z); //这一句不执行
}
//跳到这里
```
