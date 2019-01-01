---
title: Vim 插件 - 前端篇
category:
  - Vim
date: 2018-12-26 18:51:27
tags:
  - html
---
Vim是一个很炫酷的软件，它给程序员带来的不仅仅是效率，还有代码的哲学。Vim插件对于Vim更是如虎添翼，它使得vim在代码的编写中更加地高效，而从今天开始，我将通过一个系列来总结一下过去所使用过的Vim插件。  
本篇主要阐述了Vim在前端中使用的插件。

<!-- more -->

测试环境| 版本    
--------|:--  
操作系统| Ubuntu 18.04.1 LTS 
vim     | 8.0 1-1453 

### 基础插件 
> 基础插件是为了让vim变得更加高效和简单

#### Vundle
[Vundle](https://github.com/VundleVim/Vundle.vim) 是Vim包的缩写，同时也是一个Vim插件的管理工具

### Html插件
> Html插件使得写html代码时更快

#### Emment-vim
[Emmet-vim](https://github.com/mattn/emmet-vim) 是一个通过快捷键来大量减少html代码的编写的Vim插件，它类似于[Emmet](https://emmet.io/)。

##### Configure
+ 在不同的模式下有效 `let g:user_emmet_mode='n'` 有效值为`n`,`inv`,`a`
+ 仅仅在html/css下有效 
```bash
let g:user_emmet_install_global = 0
autocmd FileType html,css EmmetInstall  
```
+ 修改快捷键 `let g:user_emmet_leader_key='<C-Z>'`
+ ~~支持不同语言~~
+ ~~支持webapi~~

##### Exprience  
+ `html:5` 用于生成html5模板
+ [表达式语法](https://docs.emmet.io/abbreviations/syntax/#abbreviations-syntax)
	+ `div>p#foo$*3>a`
	+ `#` `.`与css的语法一样
	+ `$`表示递增,`*`表示乘以 
 
+ 在多行文字中快速用标签生成: 视图模式下选中多行文字，输入`<c-y> ,`,提示输入标签及可
+ `<c-y>d` 选择标签模式，并进入视图模式
	+ 插入模式下，处于左标签或者左标签后第一个字母中，触发快捷键，将会选择整个上一层标签，反之，将会选择当前标签
	+ 普通模式下，处于左标签中，触发快捷键，将会选择整个上一层标签，反之，将会选择当前标签
+ `<c-y>n` 普通模式或插入模式下，在下一个可编辑节点同时进入输入模式
+ `<c-y>N` 普通模式或插入模式下，在上一个可编辑节点同时进入输入模式
+ `<c-y>i` 在img标签内将自动生成当前图片的大小值，仅限于本地文件
+ `<c-y>m` 合并选中的行为一行
+ `<c-y>k` 删除标签
	+ 插入模式下，当处于左标签上时，会删除上一层标签，反之，删除当前标签
	+ 普通模式下，没有上述的第一种情况
+ `<c-y>/` 注释与反注释
+ `<c-y>j` 将当前标签内的标签或内容删除，结尾以`/>`结束，如果当前标签内没有任何内容且以`/>`结束，则将作用于上一层标签
+ `<c-y>a` 处于url上时，将自动生成带a标签的代码
+ `<c-y>A` 处于url上时，将自动生成带blockquote的代码
