---
title: json、XML、Protobuf
layout: doc
date:   2023-04-08 16:36:00 +0800
categories: network, protocol, tcp, udp, http
---
# json
- 原理
	- 明文
	- 基于文本格式
		- 整型、浮点数更占空间更耗时
		- 基于字符串的tag匹配
- 缺点
	- 以下几种情况性能最差
		- 跳过非常长的字符串
		- 编解码double字段
		- 解码整数
# XML
# protobuf
- 优势
	- 压缩性好
	- 序列化与反序列化快
	- 传输速度快
- 缺点
	- 性能依靠语言与解析库的实现
- 原理
	- 二进制、结构化
	- 基于数字的tag
	- 正文前有长度标记