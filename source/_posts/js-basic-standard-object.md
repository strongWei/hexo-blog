---
title: JavaScript 基本篇 - Object
categories:
  - JavaScript
date: 2019-01-07 18:58:40
tags:
---


JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。
 
### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)>并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的>知识点总结 
 
<!-- more -->

JavaScript 所有其它对象都继承自`Object`对象。
#### 原生方法分类
原生方法分为两类，分别是 `Object` 本身的方法和 `Object`的实例方法。`Object`本身的方法主要指的是直接定义在`Object`对象上的方法， `Object`实例方法指的则是定义在`Object.prototype`上的方法，它可以被`Object`实例直接使用。  
`注意：如果使用同一个名字定义了这两类方法，创建一个Object实例，并使用`.方法名`时，实例方法的优先及更高`

#### Object()
该方法实际上是一个工具方法，它可以将任意值转换为一个对象。  
什么是空对象？空对象指的是使用`Object()`传递一个空参数或`undefined`或`null`,此时的对象实际就是空对象。  
如果传入的参数是一个原始类型值，它会自动转换成原始类型的包装对象，如`Number`。

##### instanceof
该运算符用来判断一个对象是否由指定的构造函数的实例。
```js
//notice:
var k = new String('haa');
k instanceof String; //true
k instanceof Object; //true
```
如何判断一个变量是否是一个对象?
```js
function isObject(o){
	return o === Object(o);

}
```

#### Object 构造函数
与`Object()`的功能基本上一样的，都可以用来构建一个对象的实例，不同在于语义上。

#### 静态方法
静态方法，指的是在`Object`对象自身的方法。
##### Object.keys() Object.getOwnPropertyName()
`Object.keys` 和 `Object.getOwnPropertyName()`都可以用来获取对象的属性列表，不同的在于，`Object.getOwnPropertyName()` 可以获取对象不可枚举的属性，如`Array()`对象的属性`length`。

##### Object.getOwnPropertyDescriptor()
获取对象属性描述对象
> `Object.prototype` 也是一个对象，它自身的属性也都是不可遍历的

##### Object.defineProperty Object.defineProperties()
通过对象的属性描述对象，定义或修改属性，然后返回修改后的对象

##### Object.preventExtensions
使得对象无法再添加一个属性

##### Object.isExtensible
用于检查对象是否调用了`preventExtensions`

##### Object.seal
使得对象既不可以添加新属性，又不可以删除旧属性

##### Object.isSealed
检查对象是否调用`seal`  

##### Object.freeze
使得对象无法添加属性，删除属性，修改属性

##### Object.isFrozen
检查对象是否调用`freeze`

#### 实例方法
实例方法，指的是定义在`Object.prototype`的方法。

##### Object.prototype.valueOf
默认情况下，都会返回对象的本身。

##### Object.prototype.toString
它的作用是返回一个对象的字符串形式，默认会返回类型字符串。一个常用的例子，当使用`+`与字符串连接时，会调用`toString()`进行字符串的连接。

特殊应用： 精准地判断数据类型 
```js
var type = function (o) {
	var s = Object.prototype.toString.call(o);
	return s.match(/\[object (.*?)\]/)[1].toLowerCase();
}
type(null); // "null"

//通过isXXX来判断数据类型
[
  'Number',
  'String',
  'RegExp',
  'Object',
  'Array',
  'String',
  'Boolean',
  'Function'
].forEach(function(t){
	type['is'+t] = function(o){
		return type(o) === t.toLowercase();
	};
});
```

##### Object.prototype.toLocaleString
该方法用于自动返回某些地域下的特定的值。其中 `Array`, `Date`, `Number` 都自定义了。


##### Object.prototype.hasOwnProperty
用于判断该实例自身是否具有某个属性。如继承来的属性就会返回`false`。

##### Object.prototype.propertyIsEnumerable
用于判断对象某个属性是否是可遍历的,对于继承的属性一律返回`false`。

#### 属性描述对象
定义: 用于描述对象的属性，控制它们的行为。它们分别是`value`、`writable`、`enumerable`、 `configurable`、 `get`和 `set`。  

##### value
用于描述属性的值，默认值为undefined, 注意:
- 只要 `writable`和`configurable`其中一个为`true`, 则可以改动，注意`configurable`为`true`,改动只能通过`defineProperty`。

##### writable
用于描述`value`是否可改，默认是`true`

##### enumerable
用于描述属性是否可遍历， 注意:
- 如果为`false`,`for...int`、`Object.keys`和 `JSON.stringify` 不会取到该属性


##### configurable
用于描述是否可修改属性描述对象，同时还决定是否可被删除`delete`，注意：
- 如果为`false`, `value`,`writable`,`enumerable`,`configurable`不能修改
- 如果为`false`, `writable`只在由`true`改为`false`是允许的

##### get set
用于在存取时自动执行的方法
```js
var obj = Object.defineProperty({
}, 'p', {
    get: function(){

    },
    set: function(){

    }
}
); 

var obj = {
   get p(){


   }
   set p(x){

   }
};
```

##### 对象的拷贝
```js
var extend = function(from, to){
    for(var property in from){
        if(!from.hasOwnProperty(property)) continue;
        Object.defineProperty(
        to,
        property,
        Object.getOwnPropertyDescriptor(from, property);
        );
    }
    return to;
}
```

##### 对象的冻结
可以使用`seal`,`freeze`,`preventExtensions`来实现，有一些弊端：
- 对象的原型对象还是可以被修改
- 如果对象的属性值是一个对象，同样可以修改该属性值
