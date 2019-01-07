---
title: C++ 工具篇 - Cmake
tags:
- cpp
categories:
- C++
---
Cmake是C++的编译工具，它主要用于支持在多平台上的编译工作。使用者只需要写一份与平台无关的CMakeList文件，然后再根据用户平台进一步生成所需的本地化文件，真正做到一份文件，多个平中编译运行。  

本篇文章主要讲述了Cmake的一些知识和用法，并对此作出一些总结。

### Configure
``` sh
# required 最低版本要求
cmake_minimum_required(VERSION 2.8)

# 项目信息
project(Demo1)

# 编译生成可执行文件，第一个参数表示指定生成的可执行文件名, main.cpp一般都是指项目的启动文件,后面跟着多个文件，同样需要生成.o
# 但事实上一般不会用于生成多个文件
add_executable(Demo main.cpp ***.cpp)

# 查找当前目录下的所有源文件，并将名称保存到变量中
aux_source_directory(. DIR_SRCS)

# 指明需要添加到本项目的子文件夹，它的CMakeLists.txt和源代码都会被处理
# 一般用于有很多源代码文件的子目录 
add_subdirectory(math)

# 添加链接库
target_link_librariess(Demo MathFunctions)

# 生成静态链接库
add_library(MathFuncions ${DIR_LIB_SRCS})

# 设置生成文件的输出目录
set_target_properties(main PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${PROJECT_SOURCE_DIR}/BIN")
```

### Command
#### cmake
```bash
# . 表示需要执行需要生成的目录
cmake .
#  编译运行
make

``` 

### Exprience
~ ~[教程](http://www.hahack.com/codes/cmake/)~~
