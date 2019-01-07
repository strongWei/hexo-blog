---
title: Vim插件 - 基础篇  
tags:
- js  
categories:
- Vim
---
Vim是一个很炫酷的软件，它给程序员带来的不仅仅是效率，还有代码的哲学。Vim插件对于Vim更是如虎添翼，它使得vim在代码的编写中更加地高效，而从今天开始，我将
通过一个系列来总结一下过去所使用过的Vim插件。  

本篇主要阐述了Vim的基础插件，即不依赖于任何的编程语言，来提高使用vim的效率

<!-- more -->

测试环境| 版本
--------|:--
操作系统| Ubuntu 18.04.1 LTS
vim     | 8.0 1-1453

#### Vundle
[Vundle](https://github.com/VundleVim/Vundle.vim) 是Vim包的缩写，同时也是一个Vim插件的管理工具

#### Syntastic
Syntastic 通过结合其它的代码解析插件，如`jshint`，可以实现在运行或编绎前对代码进行错误的检查，从而提高编程效率。[详细教程](https://github.com/vim-syntastic/syntastic)

##### Install
使用Vundle安装即可

##### Command
###### 常用
`:SyntasticInfo` 主要用于查看当前文件在`Syntastic`是否是有效及其使用的检查器    
`:SyntasticCheck` 立即进行检查，但仍然是在保存文件的前提下  
`:SyntasticReset` 重置所有的错误  
`:lnext` 下一个错误  
`:lprevious` 上一个错误  

###### 其它  
`:Errors` 打开错误的窗口  
`:lclose` 关闭错误窗口  
`:SyntasticToggleMode` 切换模式，一般使用默认

##### Configure
我的配置
```
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1 
let g:syntastic_auto_loc_list = 1 
let g:syntastic_check_on_open = 1 
let g:syntastic_check_on_wq = 0

" - html
let g:syntastic_html_checkers = ['htmlhint']

" - js
let g:syntastic_js_checkers = ['jshint']

" - python
let g:syntastic_python_checkers = ['python']
" -- 使用python3必须用这个
let g:syntastic_python_python_exec = '/usr/bin/python'
```

##### Experience

#### YouCompleteMe
YouComplete 是强大的代码补全软件，借用一些第三方的库可以实现对不同编程语言代码的补全。[详细教程](https://github.com/Valloric/YouCompleteMe)

##### Install
0. 检查安装条件是否满足，要求vim要支持python3/python2。
1. 使用Vundle安装，时间很长。
2. 查看用法指南

##### Configure
我的配置
```
# 配置需要忽略检查的文件类型
let g:ycm_filetype_specific_completion_to_disable = {
      \ 'gitcommit': 1,
      \ 'cpp': 1
      \}
```

相关:
1. 可以通过执行 `set ft?` 来获取文件的类型

##### Exprience
0. 使用Vundle安装，打开Vim提示：`no modules found namd future`  
   这说明还没有安装成功，可能是安装还在进行中  
1. 安装成功后，打开Vim提示: `ycmd server shutdown...`  
   此时可以输入`:YcmdDebugInfo` 查找报错的文件 ，或者 `：YcmToggleLos` 直接查看报错信息。  

2. 报错信息，`ycm_core model not found`, 需要重新编译
   查下文档，说可能是`ycm_core`库已经被更新，所以会提示你要重新安装
```bash
sudo apt install build-essential cmake python3-dev
   
cd ~/.vim/bundle/YouCompleteMe
python3 install.py
```  
4. 如果需要添加其它语言的支持，必须重新执行 `install.py`

