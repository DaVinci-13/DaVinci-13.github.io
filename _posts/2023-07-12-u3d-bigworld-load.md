---
layout: post
title:  "Unity 大世界地图加载方案"
date:   2023-07-12 16:28:00 +0800
categories: unity, bigworld, loadscene
---

# 大地形渲染方案

## 资源处理
- 模型：面数更少
	- LOD
	- Amplify Impostors
- 贴图
	- minmap
	- Amplify Texture

## 方案：剔除
- 剔除
	- 遮挡
	- 视锥体
- 网格合并
- GPU计算
	- IOC
		- 它的思想就是第一步先做一个初略的遮挡裁剪列表，而后在此基础上再根据视线距离或者射线检测做进一步的细化裁剪操作

## 方案：多线程加载
- 多线程地图加载


# 问题：地形接缝方案
