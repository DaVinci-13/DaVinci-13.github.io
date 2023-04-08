---
title: 骨骼动画
layout: doc
date:   2023-04-08 16:13:00 +0800
categories: anime, skeletal
---

# 骨骼动画 Skeletal Animation
1. theory
	- 1个蒙皮影响多根骨骼
	- flow
		- mesh->Skeleton->Skinning/Rig->Pose->Animation
	- joint
		- root joint
			- 非人形骨骼root point：尾椎
	- bind animation
		- e.g.
			- 载具
	- T-Pos vs. A-Pos
2. Root motion
	- 作为mesh在屏幕外时是否更新的依据
	- 进行坐标计算时的Root空间。
3. Weighted Skinning with Multi-joints
	- 蒙皮受多根骨骼控制
	- 模型空间插值
	- 多根骨骼预定义权重
4. e.g
	- unity:Humaniod
