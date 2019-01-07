---
title: JavaScript 基本篇 - Array
categories:
  - JavaScript
date: 2019-01-07 18:58:33
tags:
---


JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。
 
### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)>并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的>知识点总结 
 
<!-- more -->

#### 构造函数
> 由于传入不同的参数会返回不同的结果，因此不建议使用
```js
var a=Array(3);
0 in a; //false
```

#### 静态方法 
##### isArray
判断是否是数组

#### 实例方法
##### valueOf toString
```js
var a=[1,2,3]
a.valueOf()  // [1,2,3]
a.toString() // 1,2,3
```

##### push pop [会改变数组]
push 在末尾添加一个或多个元素，并返回长度  
pop 删除最后一个元素，并返回该元素

##### shift unshift
shift 删除第一个元素，并返回该元素
unshift 在数组的前面添加一个或多个元素，并返回长度

##### join
将数组元素以分隔符隔开，生成一个字符串，默认分隔符是`,`
> 如果数组成员是`undefined`或`null`, 将转换成空格
```js
//将字符串以分隔符隔开
var str='helo';
Array.prototype.join.call(str,'_')

//将对象元素以分隔符隔开
var obj={
    a:1,
    b:2,
    length: 2
};
Array.prototype.join.call(obj, '-'); // 'a-b'
```

##### concat
将多个数组或其它类型值合并，将合并的元素放到最后面，并返回新的数组  
> 数组成员是对象时，是使用浅拷贝模式

##### reverse [会改变数组]
将数组的顺序颠倒，并返回改变后的数组

##### slice
a. 取出数组的一部分（终止位置不包含），生成新的数组  
b. 进行原数组的拷贝
c. `Array.prototype.slice.call` 将类似数组的对象转换成数组

##### splice [会改变数组]
从某个位置开始，删除n个元素，再插入需要的元素

##### sort [会改变数组]
对数组进行排序，或自定义数组排序, 默认是按照字典排序
```js
var a=[1,101,11];
a.sort(function(o1, o2){
    return o1-o2;  //大于0在前
})
```

##### map
a. 将数组的所有成员当成参数传入函数，然后计算，并返回一个计算后的新数组 
b. 支持传入一个对象绑定this变量
```
[1,2].map(function(elem,index,arr){

});

var b=['a','b','c'];
[1,2].map(function(e){
    return this[e]
},b);  //返回 ['b','c'], 这里是将this绑定了传入的b
```
> 空位会自动跳过函数的调用 

##### forEach
a. 用法与map一样，只不过不返回新的数组。 
b. 不支持中断操作
c. 支持传入一个对象绑定this变量
> 空位会自动跳过函数的调用 

##### filter
a. 将数组的成员传入函数，如果返回`true`, 则放进新的数组并返回
b. 支持传入一个对象绑定this变量
```js
var a=[1,2,3];
a.filter(function(elem,index,arr){
    return elem>3;
});
```

##### some every
some 将数组成员传入函数，如果某个元素计算后返回`true`, 则返回true  
every 将数组成员传入函数，如果所有元素计算后返回`true`, 则返回true
> 支持传入一个对象绑定this变量

##### reduce reduceRight
一个是从左到右处理数组，一个是从右到左处理数组，最终返回一个值
```js
[1,2,3,4,5].reduce(function(a,b,index,arr){
    return a+b;
}, 10);
//a为累积变量
//如果省略10, a 默认为第一个元素的值，b默认为第二个元素的值
//否则，a为10, b为第一个元素的值

```

##### indexOf lastIndexOf
a. 搜索给定元素在数组出现的位置，没有则返回-1  
b. 可以给定第二个参数，表示从第几个位置开始搜索  
c. 比较机制采用严格的 `===`

