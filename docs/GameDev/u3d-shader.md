---
layout:    doc
title:    Shader
---

# Shader编写

## 简介

## 语法

## 编写规范

## 优化：计算
1. 计算量
    - 避免**复杂数学**，e.g. 
        - **开方**。尝试使用sqrMagnitude（即magnitude的平方）替代magnitude，减少开平方操作
        - **向量计算**
    - 尽量把计算放在**顶点函数**
2. 计算精度：当使用CG / HLSL编写着色器时，存在三种基本的数字类型：float(32bits)，half(16bits)和fixed(11bits)：
	- 对于世界空间位置和纹理坐标，使用float精度。
	- 对于其他一切（矢量，HDR颜色等），首先使用half精度，必要时增加精度。
	- 对于纹理数据的非常简单的操作，使用fixed精度。