---
layout: post
title:  xLua加密
date:   2023-06-27 20:17:00 +0800
categories: unity, xlua
---
# LUA如何进行压缩加密
1. 打包AB
2. 压缩成一个文件：
- 读取所有文件的字节流(byte[])
- 将上述所有文件的字节流链表序列化成一个字节数组byte[]
- 压缩扰动后
- 存储成文件
- 序列化写在Editor脚本，反序列化可写在xLua源码中。