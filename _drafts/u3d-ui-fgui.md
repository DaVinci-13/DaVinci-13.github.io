---
layout: doc
title:  "FairyGUI - 学习1"
date:   2023-04-05 15:34:00 +0800
categories: Unity, fgui, UI
---

# FairyGUI
- 优点
	- 开发效率
		- 美术优化
		- 方便拼界面
	- 减少消耗
		- 内存
		- GC
			- 动态改变无GC
			- 支持
				- 透明
				- 位移
				- 旋转
			- 不支持
				- 文字图片改变
		- UI Batch->reconsturct
			- 原理
				- 动态后期优化
				- 不需要动静分离
	- 自带缓存
	- 自带图集
	- 跨平台
- 缺点