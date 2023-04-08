---
title: 刚体层次动画
layout: doc
date:   2023-04-08 14:52:00 +0800
categories: anime, Rigid Hierachical
---

# 骨骼动画 Rigid Hierachical Animation
## 2D
- 2D拆分
	- spine
- live2D
	- 网格控制
	- 深度控制
---
## 3D
- theory
	- 骨骼蒙皮绑定
	- 通过骨骼带动皮肤运动，也就是通过骨骼的移动动态计算mesh上的点的位置
- e.g.
	- unity：Generic
		- 1个顶点最多控制n个骨骼
			- unity设置
				- 1
				- 2
				- 4
				- auto
		- 无法动画重定向