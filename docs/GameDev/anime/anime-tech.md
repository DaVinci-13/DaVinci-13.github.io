---
title: 高级动画技术
layout: doc
date:   2023-04-08 16:13:00 +0800
categories: anime, technology
---

# Animation Blending 动画融合

## Cross Fade，淡入淡出
- Curze
	- smooth transition
	- Frozen transition
## 切换
- 插值
- 权重
## timeline
- 归一化
- Timeline Alignment
	- 滑步问题
		- 速度与动画匹配
## Blend Space
- Delaunay Triangulation
	- 根据点进行三角形划分
- 动画插值
- Unity：BlendTree
## Blending
- Lerp
- Skeleton Mask
- Additive Blending
	- 只存储动画变化量
	- problem
		- 过度叠加动画

# Animation State Machine, ASM, 动画状态机
1. Definition
	- ClipNode
	- BlendSpaceNode
2. Layered
	- 多层状态机
	- 每层状态机控制不同部分

# Animation Blend Tree 动画树
- 参数控制
- 事件

# IK，逆向动力学
- 启发式算法
- CCD, Cyclic Coordinate Decent
- FABRIK, Forward And Backward Reaching Inverse inematics
- problem
	- 避免自我交叠
	- 移动预测
	- 更自然的人类行为学

# Face Animation

- theory
	- Face is Driven by Complex Muscle System
	- High Precision Requirements
- how to
	- Facial Action Coding System
		- Action Units Combination
		- 28 Core Action Units
		- problem
			- blending
	- Blend Shape
		- Morph Target Animation
		- 局部网格变换
			- Create AU Key poses only store vertexes different from  the neutral pose
	- Complex Facial Skeleton
	- UV Texture Facial Animation
		- 部分偏2D
	- Muscle Model Animation
- problem
	- 采样问题
		- 数据从texture到mesh

# Animation Retargeting 动画重定向
1. 骨骼动画重定向
- 一套动画应用与多种Model
- TermInology
	- Source Character/Animation
	- Target ^
- 骨骼偏差
	- 相对偏移
		- 相对于BindingPose（T-pos、A-pos）
	- 忽略原骨骼与目标骨骼关节偏差
	- 位移动画考虑骨骼偏差
- 骨骼映射
2. 问题
    1. 双脚浮空问题
	- 位移动画参考身高
		- 计算动画腰线离地面距离
	- IK
	- 某些角色在重定向之后的动画中表现为脚不贴地，和地面之间有缝隙，原始动画中没有这一问题。如果你理解了动画重定向的原理，那么当原始动画没有问题，而重定向之后的动画存在问题，有两种可能——一种是重定向算法存在问题，另外一种是参考姿势存在问题。我们在没有代码授权的前提下无法查看和修改Unity引擎的重定向实现代码，而且Retargeting功能已经发布了这么久，理论上大部分的Bug都应该已经修复了。。。在Avatar的Configuration界面中，除了设置骨骼的映射关系之外，还可以设置T-Pos的姿势，这里我们可以对参考姿势做微调，如下图所示：
    2. Self mesh penetration 角色自穿插问题
    3. Self contact constrains
	- e.g.
		- hands when clap
	- 第一个是角色的武器或者飘带在使用Humanoid类型的动画系统之后不会移动了，或者移动的位置有了很大的偏差。这时候可以在动画文件的属性设置里，查看Mask下的Transform选项，里面可能存在没有被勾选的骨骼。
    4. 人体平衡问题
    5. 随机数问题
	第二个是角色的武器在动作中出现了乱飘的问题，与手部无法紧密地绑定在一起。这是由于我们最初为了方便美术制作武器的动作，把其父骨骼设置给了盆骨这样一根相对稳定的骨骼，但是经过Retargeting计算之后，由于角色身材不同产生了一些偏差导致了这一问题。最终我们还是把武器骨骼的父骨骼设置为手部的骨骼，才解决了这一问题。
3. 表情动画重定向
- 添加约束
	- 拉普拉斯算子
