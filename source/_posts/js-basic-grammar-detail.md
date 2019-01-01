---
title: js-basic-grammar-detail
categories:
  - JavaScript
date: 2019-01-01 08:37:31
tags:
---

JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己>的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。
 
### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)并结合过
    去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的知识点总结 
 
<!-- more -->

#### 数据类型转换

##### Number  
主要分为对原始类型值的转换和对对象的转换。
###### 原始类型值的转换
`Number()` 转换原始值的规则没什么可说的，有一点需要注意的是对字符串的转换，只要字符串中有一个字符无法转成数值，就会返回 `NaN` ,这也是它与 `parseInt()`的最大区别

###### 对象
**规则**   只要对象不是空的数组或者是只有单个值的数组，就一定会返回`NaN`   
**转换原理**   首先会先调用对象自身的 `valueOf()`, 如果返回原始类型的值，则立即调用`Number()`, 反之，再调用对象的 `toString()`，如果返回原始类型的值，同样调用 `Number()`, 否则直接报错。

##### String
主要分为对原始类型值的转换和对对象的转换。
###### 原始值的转换  
```js
String(0) // '0'
String('abc') // 'abc'
String(false) // 'false'
String(undefined) // 'undefined'
String(null)	// 'null'
```

###### 对象
**规则** 如果是对象，返回一个类型字符串，如果是数组，返回该数组的字符串形式  
**转换原理**  与 `Number` 相反，它先调用的是 `toString()`, 再根据情况调用 `valueOf()`


##### Boolean
规则： 除了`undefined`, `null`, `0`, `NaN`, ''之外，其它都返回true 

##### 自动转换
**情形**  
- 不同类型的数据进行运算
- 非布尔值类型进行判断
- 非数值类型进行使用数值运算符`+`/`-`


#### Error对象
##### 属性
包括`message`,`name`,`stack`, 其中 `message`是标准的，其它是非标准的

##### 派生对象
1. SyntaxError 表示的是语法出现错误  
2. ReferenceError 有两种情况会出现，一种是引用不存在的变量，第二种是将一个值分配到一个无法分配的对象，如函数的运行结果或`this`
3. RangeError 表示一个值超出有效的范围，有三种情况下出现，一种是数组的长度为负数，第二种是`Number`对象的方法参数超出范围，第三种是函数堆栈超出最大值
4. TypeError 表示变量或参数不是预期的类型，有两种情况下出现，一种是new 原始类型值，第二种是调用对象不存在的方法
5. URIError 表示URI相关函数的参数不正确，主要有下面这些函数：`encodeURI()`,`decodeURI()`,`encodeURIComponent()`,`decodeURIComponent`,`escape()`,`unescape()`
6. EvalError 表示`eval`函数没有被正确执行，该错误已不再使用

##### 自定义错误
```js
function UserError(message){
	this.name = 'UserError';
	this.message = message || 'xxx';
}

UserError.prototype = new Error();
UserError.prototype.constrctor = UserError;

//调用 
new UserError('hello');
```

##### Try
可以抛出任意值

##### Finally
> 触发Catch立即转入Finally的两个条件: return 语句，throw 语句  
  
[示例](https://wangdoc.com/javascript/features/error.html)


#### Console 对象
##### console.log
1. 可传递多个参数, 用于输出多个变量
2. 可进行格式化输出  
-`%d` 整数   
-`%i` 整数   
-`%s` 字符串   
-`%c` `CSS` 格式化    
-`%f` 浮点数  
-`%o` 对象的链接  
3. console.info  
与 log 类似，输出时左边带有蓝色的标签
4. console.debug
与 log 类似，一般不显示，必须调整浏览器的level为`verbose`才会显示 
5. console.warn
与 log 类似，输出时有黄色的背景色
6. console.error
与 log 类似，输出时有红色的背景色
7. 如何自定义输出
```js
['log','info','warn','error'].forEach(function(method){
	console[method] = console[metood].bind(
		console,
		new Date().toISOString()
	);	
});

console.log('error'); //将会在前面显示时间
```

##### console.table
对于某些复合型的数据，可以用表格来显示

##### console.count
计算被调用了多少次，可以传递一个参数作为标签

##### console.dir console.dirxml的作用
`console.dir` 用于显示一个对象的所有属性，对Dom对象很有用  
`console.dirxml` 用于打印Dom节点，如果不是Dom结点，跟`console.dir`一样

##### console.assert
接收两个参数，第一个参数是表达式，第二个参数是输出信息，如果第一个参数的结果为`false`，则输出信息，但不会中断程序

##### console.time console.timeEnd
计时器，用于计算代码的执行时间，传递一个参数作为计时器名称

##### console.group console.groupEnd console.groupCollapsed
用于输出信息的分组, `group()`和`groupCollapsed()`可传递一个参数。

##### console.clear console.trace
`console.trace`显示当前执行代码的在堆栈中的调用路径
`console.clear`表示清空, 如果选中控制台的`Preserve log`选项，则不起作用

##### ~~控制台命令行 API~~


##### debugger
如果正在运行除错器，当代码运行到这里时，会立即中断并进入调试

