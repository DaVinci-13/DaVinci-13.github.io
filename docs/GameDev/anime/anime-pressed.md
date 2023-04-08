---
title: 动画压缩
layout: doc
date:   2023-04-08 14:52:00 +0800
categories: anime, press
---

# 动画压缩技术

## 动画制作
- DCC
	- mesh->skeleton binding(->Add joints->)Skinning->Animation Creation->Exporting
		- Skinning
			- 自动计算
			- 手动矫正
		- Exporting 
			- 位移曲线
			- 格式
				- FBX
- 动作捕捉
	
## 动画计算
- Rotate 旋转
	- Euler 欧拉角
		- 严格旋转顺序
		- 问题
			- 万向节死锁
			- 插值问题
			- 多重旋转叠加问题
			- 任意轴旋转问题
	- Quaternion 四元数
		- 子主题 1
		- 子主题 2
		- Rotation to Quaternion
- translate 平移
- Scale 放缩

## 动画存储
- 关节 本地坐标系
- 压缩
	- Dof Reducing 减少自由度（需要存储的位移旋转缩放）
		- keyframe 关键帧插值
		- Catmull-Rom Spline 卡特默曲线
			- 经验值函数
			- 逼近真实旋转计算
		- 定点数模拟浮点数
			- 压缩四元数
			- 浮点数：32bit
		- Error Propagation 误差蝴蝶效应
			- e.g.
				- 抖动问题
			- 敏感度设置
				- 误差评估
			- 误差补偿
	- e.g.
		- unity
			- Curves 动画曲线
## pipeline
- 蒙皮动画
	- 蒙皮新坐标=模型世界变换矩阵*新关节位置*关节顶点逆矩阵
- 动画插值
	- 旋转
		- NLERP：线性插值+归一化+最短路径判断
			- 最短路径判断：点乘
		- SLERP：角度插值
			- 三角函数计算消耗性能，必须查表
		- 结合
			- 夹角小：NLERP
			- 夹角大：SLERP