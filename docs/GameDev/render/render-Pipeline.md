---
title: 渲染流水线
layout: doc
date:   2023-04-08 14:09:00 +0800
categories: render, graphics, pipeline
---

# 渲染流水线
## 应用阶段
- 粗粒度剔除
	- 遮挡剔除
	- 视锥体剔除
- 渲染设置
- 准备数据
## 几何阶段
- Vertex Shader
- Tesselation Shader
- Geometry Shader
- 视锥体裁剪
- MVP
## 光栅化阶段
- 渲染三角形
	- 设置
	- 遍历
- AA 抗锯齿
## 片元处理 Fragment Shader
- 三大测试
	- AlphaTest 裁剪测试
	- Stencil Test
	- Depth Test
- 颜色混合
## 后处理