---
title: JavaScript 基本篇 - 包装对象
categories:
  - JavaScript
date: 2019-01-07 18:58:56
tags:
---


JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。
 
### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的知识点总结 
 
<!-- more -->

#### 静态方法 
##### fromCharCode
用于将一个或多个unicode码点(U+0000-U+FFFF)转换成Unicode字符串  
注意： 如果超过U+FFFF, 则会返回错误的字符串，这时可以将它拆分成两个
```js
//原本是0x20BB7
String.fromCharCode(0xD842, 0xDFB7)
```

#### 实例方法
##### String.prototype.charAt
跟`[]`是一样的

##### String.prototype.charCodeAt
是`fromCharCode`的逆操作  
注意：如果是超过U+FFFF的字符，应该将两个合并到一起，如何~~合并~~

##### String.prototype.concat
用于连接多个字符串,并返回新的字符串

##### String.prototype.slice
用于取出子字符串，并返回新的字符串

##### String.prototype.substring
与slice很像，不建议使用

##### String.prototype.substr
与slice,substring很像，不同在于第二个参数是长度。

##### String.prototype.indexOf String.prototype.lastIndexOf
搜索字符串的开始位置

##### String.prototype.trim
会去除字符串前后的(空格，`\t`,`\v`,`\r`,`\n`)，并返回新的字符串

##### String.prototype.toLowerCase String.prototype.toUpperCase
全部转大写或小写，并返回新的字符串

##### String.prototype.match
a. 确定原字符串是否匹配某个字符串，返回一个数组，成员为匹配的第一个字符串，如果没有匹配，返回`null`  
b. 返回的数组中，`index` 属性表示匹配开始的位置，`input`表示原字符串

##### String.prototype.search
与 `match`类似，不同在于没有匹配时返回-1

##### String.prototype.replace
用于替换匹配的子字符串，一般情况下只替换第一个，除非使用正则表达式

##### String.prototype.split
根据分割符分割字符串为数组，第二个参数指定时表示要返回的数组成员数

##### String.prototype.localeCompare
根据不同国家的自然语言规则进行比较，并返回一个整数（大于0则表示第一个字符串大于第二个字符串)
```js
'ä'.localeCompare('z', 'de'); //-1
```
