---
layout:    doc
title:    ILruntime
date:   2023-04-05 17:47:00 +0800
categories: Unity, light, lightmap
---

# ILruntime
## 优势
1. 无缝访问C#
	- 跨域继承
	- 泛型支持
	- 无需抽象API
2. 执行效率
	- L#*10~20
	- CLR绑定=sLua*2
3. 调试插件
4. vs. Lua
	- Lua
		- 成熟
		- 历史原因
		- 熟悉Lua
---

## 步骤
加载dll
- 读取streamingAsset/*.dll到内存
- appdomain.LoadAssembly():主工程读取dll到解释器
- 初始化CLR
- OnHotFixLoaded()执行逻辑处理
---

## 项目结构
- Unity主工程
	- 不能热更
	- MonoBehavior
	- 加载dll
- HotFix_Project.dll
	- 热更工程
	- Unity将"~"结尾的文件与文件夹在Editor下隐藏
---

## 概念
1. 跨域
	- 委托
		- 额外适配器/转换器
	- 继承
		- 继承适配器
			- 主工程
			- 注册
	- 原理
		- appdomain 程序域
		- 反射
2. 反射转换
	- 类型映射
3. 高性能
	- CLR重定向
	- CLR绑定
---

## 原理
- Mono.Cecil
- IL托管栈
	- unsafe
	- 非托管内存
---
## 性能优化
- Release模式测试
- 关闭Development Build
- 避免GC
	- 取代默认反射
		- CLR绑定
		- InvocationContext
	- 重新实现基于IL托管栈的值类型绑定
	- 避免频繁调用可变参数列表
		- 可变参数列表原理：new 数组
---

## 解决方案
- 不依赖于MonoBehavior的框架
- 自动化CLR绑定代码生成
- Addressable

- 原理
	- dll