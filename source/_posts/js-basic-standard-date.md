---
title: JavaScript 基本篇 - 包装对象
categories:
  - JavaScript
date: 2019-01-07 18:59:27
tags:
---


JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。
 
### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的知识点总结 
 
<!-- more -->

#### 普通函数 Date()
永远返回当前时间的字符串

#### 构造函数
##### 求值
求值时自动调用`toString`，是与其它对象的最大不同

##### 参数
- year, 使用四位数，如果 写成两位数或是一位数，则表示 `1900` 加上这个值，如果是负数，则表示公元前
- month 0-11
- day 1-31
- hour 0-23
- minimu 0-59
- second 0-59
- minsec 0-999

> 注意：如果参数超出范围，会自动进行折算

#### 日期的运算
使用减法时，返回的是间隔的毫秒数，使用加法时，返回的是字符串连接的结果

#### 静态方法 
##### Date.now
时间戮，精确到毫秒

##### Date.parse
日期字符串的解析，成功则返回距离零点的毫秒数，失败则返回`NaN`

##### Date.UTC
返回是距离零点的毫秒数，参数用法与 Date() 构造函数一样，不同的是参数会被解析成UTC时间

#### 实例方法
[链接](https://wangdoc.com/javascript/stdlib/date.html#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95)
