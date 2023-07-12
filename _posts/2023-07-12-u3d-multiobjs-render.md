---
layout: post
title:  "Unity 大量物体渲染方案"
date:   2023-07-12 16:21:00 +0800
categories: unity, render, multi-objs
---

# 大量物体渲染问题

## 大量物体
- DOTS


## 动画
- playable
- 动画烘焙
	- 烘焙动画的顶点位置变换
	- 烘焙动画的骨骼变换
	- 缺点
		- 贴图内存大小与顶点数有关
	- 解决
		- 内存问题
			- 编解码压缩动画贴图
		- 支持不用的动作、属性
			- 生成新材质设置属性
			- 对uniform进行定制化的处理
				- MATERIAL PROPERTY BLOCKS
				- 在1个drawcall下，开辟了专门的区域，用来存储指定的数据，而不是粗暴的用unity之前的material方式来实现

## 待解决问题
- 阴影渲染