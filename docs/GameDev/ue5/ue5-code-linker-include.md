---
title:    Linkers, Headers and Includes
layout:    doc
date:   2023-08-09 17:30:00 +0800
categories:    ue5, code, Design Mode
---

# Compilation Steps
## Standard C++ Compilation Steps
|Step|FileType|Content|
|---|---|---|
|(Original)|.cpp & .h|C++代码+头文件|
|Preprecessor|.i|合并C++代码和头文件|
|Compiler|.obj|二进制代码文件|
|Linker|.exe|可执行程序|

## UE Compilation Steps
|Step|FileType|Content|
|---|---|---|
|Unreal Header Tool|.cpp & .h|UHT代码、C++代码、头文件|
|标准C++编译步骤|... ...|... ...|

# Unreal Header Tool (UHT)
## Blueprint Callable
蓝图可交互