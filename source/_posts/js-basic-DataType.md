---
date: 2019-01-01 08:37:38
title: JavaScript 基础篇 - 数据类型
tags:
categories:
- JavaScript
---
JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己>的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。
 
### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的知识点总结 
 
<!-- more -->

#### 分类
主要分为6种数据类型，包括`number`,`string`,`boolean`,`null`,`undefined`, `object`, 其中`object`又分为三种，包括独立的对象，`array`, `function`。

#### typeof
`typeof` 标志符主要用于查看js变量的类型，但是它有一些缺点:
+ 认为数组的类型是 `object`
+ 对于一些原始类型的包装对象，如`Number,`String`，无法正确判断原始类型的值

#### undefined 和 null
undefined表示的是变量未定义，但已经声明，null则表示空，需要注意的是：
```js
typeof null == 'object'
typeof NaN == 'number'

Number(null) == 0
Number(undefined) == NaN
```

#### 数据类型转换后为 `false`
包括 `0`, `false`, `null`, `undefined`, `NaN`, ''。

