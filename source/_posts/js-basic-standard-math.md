---
title: JavaScript 基本篇 - Math库
categories:
  - JavaScript
date: 2019-01-07 18:58:44
tags:
---


JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。
 
### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的知识点总结 
 
<!-- more -->

#### 静态属性
- Math.E
- Math.LN2
- Math.LN10 
- Math.LOG2E
- Math.LOG10E
- Math.PI
- Math.SQRT1_2
- Math.SQRT2

#### 静态方法 
##### Math.abs
绝对值

##### Math.max Math.min
返回参数列表中的最大值或最小值，空时返回-Infinity或Infinity

##### Math.floor Math.ceil
分别返回小于参数值的最大整数和最小整数
```js
function toInteger(x){
    x = Number(x);
    return x>0 ? Math.floor(x) : Math.ceil(x);
}
```

##### Math.round
用于四舍五入，注意: 当为负数时
```js
Math.round(-1.5) //-1
```

##### Math.pow
求一个数的多少次幂的结果

##### Math.sqrt
平方根

##### Math.log
求一个数以`e`为底的自然对数值

##### Math.exp
求`e`的参数次方

##### Math.random
返回 0到1之间的随机数，可能等于0,但一定小于1
```js
//生成随机数

//生成随机整数

//生成随机字符串
```

##### 三角函数
- Math.sin
- Math.cos
- Math.tan
- Math.asin
- Math.acos
- Math.atan

