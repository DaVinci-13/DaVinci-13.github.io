---
layout:    doc
title:    合批
date:   2023-04-05 17:27:00 +0800
categories: render, batch, Drawcall
---

# Batching

## 合批原理

### 1. Glossary

- setpasscall
	- 渲染状态切换
	- 材质不一致时出现一次调用
	- 同材质球不同pass出现调用
- Drawcall
	- CPU调用一次GPU绘制函数
	- 多个drawcall可以合并batch
- batch
	- 不同mesh同材质在满足情况条件下可以合批，但不降低drawcall
		- 合并顶点数据

### 2. 渲染流程
CPU设置渲染状态SetPassCall，然后提交渲染命令Drawcall，将前两者交给GPU(Batch)后进行渲染  

## Dynamic 动态合批

### 1. 简述：
将共享同一材质多个模型合并为一个模型

### 2. 推荐使用场景：
细碎的面数较少的多个动态对象

### 3. 触发时机：
自动

### 4. 缺陷：

1. 使用限制： 单次不超过900个float4的顶点属性或255个顶点网格； 

2. 无法生效条件：  
    - Scale负值;  
    - 不同材质实例;  
    - 需要读取光照贴图;  
    - 延迟管线;  
    - 多pass. 

 
## static 静态合批

### 1. 简述：
将Static标记且shader相同的物体预先进行坐标转换并合并模型，运行时不进行坐标转换。

### 2. 注意：
降低Batch，不降低Drawcall。

### 3. 推荐使用场景：
不会修改的静态建筑与植被

### 4. 缺陷： 
1. 使用限制：  
    - 64k verticles和64k indices  
    - OpenGL ES：48k indices  
    - macOS：32k indices  

2. 无法生效条件  
    - 状态修改(gameObject.activeSelf)  
    - 材质参数修改(sprite.alpha)  
    - 坐标移动(transform.***)  
    - Scale负值  
    - 内存问题  
    - 相同对象不同应用在运行时创建不同副本  
    - 如果开启Mesh优化，Unity会在生效对象的顶点缓冲区删除所有未被任何shader变体应用的数据，可能造成功能问题


## GPU Instancing

### 1. 简述
只提交一个mesh和材质，但提交多个实例的差异信息，对同一个mesh在GPU进行变换绘制  

### 2. 使用限制
单次最大处理数量：1023个对象

### 3. 推荐使用场景：草地

### 4. 缺陷
1. 无效条件
    - 穿插遮挡
2. 缺陷
    - GPU Instancing无法充分利用GPU资源分配，当mesh面数过低时可能反而降低运行效率
    - 一般低于256个顶点的网格不适用
    - 相同Mesh间的合批


## SRP Batch

### 1. 简述
将Buffer拆分，通过降低对不需要更新的Buffer的更新频次降低SetPassCall数量与开销，以进行加速   

### 2. 特征
不降低Drawcall

### 3. 缺陷
1. 无法生效条件
    - 材质参数修改，包括MaterialPropertyBlock临时修改
    - 打断
	    - 多pass
	    - 变体
2. 缺陷
    - 影响FrameDebugger查看
    - 实际优化效果因环境差异导致效果不一定明显
    - 参数数量灵活度低:不允许变体