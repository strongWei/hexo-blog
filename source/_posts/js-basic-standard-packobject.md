---
title: JavaScript 基本篇 - 包装对象
categories:
  - JavaScript
date: 2019-01-07 18:58:51
tags:
---


JavaScript说起来挺简单，但实际上又有它自己的独特的深度。如今JavaScript不仅仅能够在网页上独挡一面，还能够用运用到app的编写上，甚至在后端的领域也能有自己的独到之处。因此学习JavaScript变得越来越重要。而从今天开始，我将通过一个系列来总结一下自己的学习成果和实际经验。
 
### Knowledge  
> 这里的知识点主要是通过学习[JS教程](https://wangdoc.com/javascript)并结合过去自己零零碎碎的知识来总结一下自己忽略的知识点，并不是完整的知识点总结 
 
<!-- more -->

#### Number String Boolean
`new xxx()` 与 `xxx()`的区别  
第一个是转换成对象，第二个是转换成相应的原始值

#### 自动转换机制
当原始对象调用包装对象的属性和方法时，将自动转换成只读的包装对象，并在使用后销毁实例
 
