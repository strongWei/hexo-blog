---
title: JSHint 配置
tags:
  - js
  - vim
categories:
  - 工具
date: 2019-01-02 10:33:45
---

JSHint主要用于对JavaScript代码的检验，配置上Syntastic在Vim的使用，可以实现对代码进行检查。  

本文主要总结自己使用JSHint的经验，并不是介绍如何使用JSHint, [教程](https://jshint.com)在此。

<!-- more -->

### 安装
```bash
npm install -g jshint //全局安装
```

### 配置
[详细配置](https://jshint.com/docs/options)

我主要是将配置写在`package.json`文件内，使用的配置如下:
```json
{
        "jshintConfig": {

                "undef": true,  //未声明时
                "unused": true, //未使用时
                "eqeqeq": true, //强制使用 === 或 !==
                "curly": true,  //强制块使用 {}
                "esversion": 5, //支持的es的版本，主要有3,5,6
                "freeze": true, //对内置对象的prototype里的属性进行重写时
                "futurehostile": true, //未来js版本更新可能会导致发生改变时会提示
                "devel": true  //允许使用console, 处于开发模式，如果是处于其它环境时可以修改变量
        }   
}
```

~~html里的js代码如何检测~~
