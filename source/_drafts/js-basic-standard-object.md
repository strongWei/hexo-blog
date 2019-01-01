---
title: JavaScript 基本篇 - Object
tags:
categories:
- JavaScript
---

### Knowledge
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
