---
title: JavaScript 基础篇 - 数组
tags:
categories:
- JavaScript
---
JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。

### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的知识点总结  

<!-- more -->


#### 本质
数组的本质上是一种特殊的对象，因此`typeof [] == 'object'`

#### length 属性
`length` 在JavaScript的内部存储形式是32位的整数，保存数组的元素个数  
  
如何改变数组的大小
```js
var arr = [1,2,3];
arr.length = 2;  //会删除 3

arr.length = 10; //将会自动填充成一个长度为10的数组，每项未设置
		 //的值为 undefined
arr.length = 0;  //清空数组 
```
  
如何为数组添加属性
```js
a['p'] = 'abc' //此时length属性没有发生改变

//如果数组的键名是非法的数值，该键名会自动转换为字符串
```

#### in
可以用于判断数组中是否有该键名

#### for...in
它不仅可以遍历数组的键名，还可以遍历出数组的属性，如`a['p']=12`的`p`  
   
如果想要遍历数组的值，最好使用用循环体或`forEach`来实现

#### 空位
实现  
```js
var a = [1,,2]; //length 为3

var b = [1,,];  //length为2, 当最后一个也为空位是，直接忽略
```
  
空位的默认值都为`undefined`, 使用`delete` 会删除一个数组成员，形成空位
  
数组的空位与数组的某一项的值是`undefined`的区别？
如果是空位，使用`forEach`,`for...in`,`Object.keys`都会跳过空位，如果是`undefined`则不会。

#### 类似数组的对象
定义  
只有对象中有`lenght`这个属性，就可以称为这个对象为类似数组的对象，类似数组的对象并不是数组，因为它们不具备数组特有的方法

如何实现  
```js
var obj = {
 0: 'abc',
 1: 'abc',
 2: 'abc',
 length: 3
};
```

实例  
主要有三个实例，包括 `arguments`, DOM元素集和字符串。  

虽然它们不是数组，但是有两种方式可以让它们使用数组的方法，一种是使用 `Array.prototype.slice.call(arrayLike)` 将它们变成真正的数组，第二种是使用 `Array.prototype.方法名.call()`。  

这两种方法的区别是第二种的效率比较慢。
```js
Array.prototype.forEach.call('abc', function(chr){
	console.log(chr);
});
```


