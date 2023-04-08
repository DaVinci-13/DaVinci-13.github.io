---
title: Game Develop
layout: doc
permalink: /gamedev/
---


# GamePlay

- Unreal

- Unity

    - 性能优化

        - 渲染

	        - drawcall
		        - [Batcher](./render/render-batch.md): dynamic、static、GPU Instancing、SRP Batcher
		        - 减少[复杂计算](./render/render-shader.md)
		        - 模型网格的裁减与合并
			    - 字符图集
			    - 特效清理
		        - [lightmap](./u3d/u3d-lightmap.md)
		        
	        - overdraw
			    - [earlyZ & preZ](./render/render-earlyZ-and-preZ.md)
		        - [Partical System](./u3d/u3d-ParticalSystem.md)
		        - [AlphaClip & AlphaBlend](./render/render-AlphaClip-and-AlphaBlend.md)

	        - 带宽

		        - [model](./art/art-Modeling.md)
		            - 降低复杂度
			        - [lod](./u3d/u3d-lod.md)

		        - [texture](./art/art-texture.md)
		            - 程序化纹理 
		        - SharedMaterial 共享材质

        - 脚本

	        - [UGUI Batch](./u3d/u3d-render-ugui.md)
	        - [GC](./cs/clr-gc.md)
	        - [u3d优化](./u3d/u3d-optimize.md)

    - 分析工具
	    - [Stats](./u3d/u3d-stats.md)
        - [Profiler](./u3d/u3d-profiler.md)			
	    - Profiler Analysis
	    - Frame Debugger

    - Unity  生命周期(本质：委托异步回调)
    
	- Component
	    - [UI](./u3d/u3d-ugui.md)
		    - [TextMeshPro](./u3d/u3d-textmeshpro.md)
	    - Camera
	    - [Transform](./render/render-transformation.md)
	    - 【Time】

		- Input
			- InputManager
			- InputSystem

	- [ScriptableObject](./u3d/u3d-ScriptableObject.md)
	
    - [UnityEditor](./u3d/u3d-editor-scripting.md)

    - 插件
	    - LogViewer
	    - EasyTouch
	    - DOTween
    	- Spine
	    - [FGUI](./u3d/u3d-fgui.md)
	    - Cinemachine
    	- [Odin](./u3d/u3d-odin.md)
	
	- [DOTS](./u3d/u3d-dots.md)
	
	- 资源管理
	    - [Resources](./u3d/u3d-resources.md)
	    - [AssetBundle & Addresable](./u3d/u3d-addresable.md)

    - 物理
		- [碰撞](./physics/physics-collision.md)

    - 异步
	    - [C#线程](./cs/cs-thread.md)
	    - [C#异步](./cs/cs-async.md)
	    - [Unity协程](./u3d/u3d-corotinue.md)
		
    - [热更新](./u3d/u3d-hotpatch.md)
		- 脚本热更新方案
		    - [xLua](./u3d/u3d-hotpatch-xlua.md)
		    - [ILruntime](./u3d/u3d-hotpatch-ilruntime.md)
		    - [hybridCLR](./u3d/u3d-hotpatch-hybridclr.md)

	- [原生交互:Android and IOS](./u3d/u3d-Android-and-IOS.md)

### Shading

- 图形学
	- 渲染
	    - [渲染流水线](./render/render-Pipeline.md)
	        - [u3d渲染管线](./u3d//u3d-pipeline-base.md)
	            - [URP](./u3d/u3d-pipeline-URP.md)
	            - [HDRP](./u3d/u3d-pipeline-HDRP.md)
	    - 渲染技术
		    - [体渲染](./render/render-volume.md)
		    - [视差](./render/render-parallax.md)
		    - [风格化](./render/render-stylized.md)
		- [后处理](./render/render-postprocess.md)
		- [Gamma](./render/render-gamma.md)
		- ShaderLab
		    - [MetaPass](./u3d/shaderlab-metapass.md)
			- [Shader变体](./u3d/shaderlab-variant.md)
 
	- 几何
		- [MVP变换](./render/render-mvp.md)
		- [向量计算](./render/render-transformation.md)

	- 光线追踪
		- [PBR](./render/render-pbr.md)

	- 动画模拟


### 动画
- [通用](./anime/anime-index.md)
- 动画类型
	- [序列帧动画](./anime/anime-sequence.md)
    - [骨骼动画](./anime/anime-skeletal.md)
    - [顶点动画](./anime/anime-vertex.md)
    - [表情动画](./anime/anime-morph.md)

		- 蒙皮动画

			- theory

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

			- Root motion

				- 作为mesh在屏幕外时是否更新的依据
				- 进行坐标计算时的Root空间。

			- Weighted Skinning with Multi-joints

				- 蒙皮受多根骨骼控制
				- 模型空间插值
				- 多根骨骼预定义权重

			- e.g

				- unity:Humaniod

		- 基于物理的动画

			- theory

				- Ragdoll 布娃娃系统
				- Cloth and Fluid simulation
				- IK，Inverse Kinematics

	- 动画制作

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

	- 动画系统

		- 动画计算

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

		- 动画存储

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

		- pipeline

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

	- 高级技术

		- Animation Blending 动画融合

			- Cross Fade，淡入淡出

				- Curze

					- smooth transition
					- Frozen transition

			- 切换

				- 插值
				- 权重

			- timeline

				- 归一化
				- Timeline Alignment

					- 滑步问题

						- 速度与动画匹配

			- Blend Space

				- Delaunay Triangulation

					- 根据点进行三角形划分

				- 动画插值
				- Unity：BlendTree

			- Blending

				- Lerp
				- Skeleton Mask
				- Additive Blending

					- 只存储动画变化量
					- problem

						- 过度叠加动画

		- Animation State Machine, ASM, 动画状态机

			- Definition

				- ClipNode
				- BlendSpaceNode

			- Layered

				- 多层状态机
				- 每层状态机控制不同部分

		- Animation Blend Tree 动画树

			- 参数控制
			- 事件

		- IK，逆向动力学

			- 启发式算法
			- CCD, Cyclic Coordinate Decent
			- FABRIK, Forward And Backward Reaching Inverse Kinematics
			- problem

				- 避免自我交叠
				- 移动预测
				- 更自然的人类行为学

		- Face Animation

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

		- Animation Retargeting

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
			- 问题

				- 双脚浮空问题

					- 位移动画参考身高

						- 计算动画腰线离地面距离

					- IK
					- 某些角色在重定向之后的动画中表现为脚不贴地，和地面之间有缝隙，原始动画中没有这一问题。如果你理解了动画重定向的原理，那么当原始动画没有问题，而重定向之后的动画存在问题，有两种可能——一种是重定向算法存在问题，另外一种是参考姿势存在问题。我们在没有代码授权的前提下无法查看和修改Unity引擎的重定向实现代码，而且Retargeting功能已经发布了这么久，理论上大部分的Bug都应该已经修复了。。。在Avatar的Configuration界面中，除了设置骨骼的映射关系之外，还可以设置T-Pos的姿势，这里我们可以对参考姿势做微调，如下图所示：

				- Self mesh penetration 角色自穿插问题
				- Self contact constrains

					- e.g.

						- hands when clap

					- 第一个是角色的武器或者飘带在使用Humanoid类型的动画系统之后不会移动了，或者移动的位置有了很大的偏差。这时候可以在动画文件的属性设置里，查看Mask下的Transform选项，里面可能存在没有被勾选的骨骼。

				- 人体平衡问题
				- 随机数问题

					-  第二个是角色的武器在动作中出现了乱飘的问题，与手部无法紧密地绑定在一起。这是由于我们最初为了方便美术制作武器的动作，把其父骨骼设置给了盆骨这样一根相对稳定的骨骼，但是经过Retargeting计算之后，由于角色身材不同产生了一些偏差导致了这一问题。最终我们还是把武器骨骼的父骨骼设置为手部的骨骼，才解决了这一问题。

			- 表情动画重定向

				- 添加约束

					- 拉普拉斯算子

- unity动画

	- Mecanim
	- Playerable动画

- unreal动画
- 3dmax
- maya
- spine

### 网络

- 协议

	- 长连接

		- TCP

			- 三次握手
			- 四次挥手

		- UDP

			- 改良：kcp

				- 可靠，有序

			- 不可靠
			- 广播

		- 一次连接可以发送多个数据包，没有数据时要检测心跳

	- 短链接

		- HTTP
		- 需要时才建立连接，发送数据完成后马上断开

- 同步

	- 状态同步

		- 快照同步

			- 可以忽略几个客户端，被忽略的几个实行AI预测
			- 服务器维护一个模拟的世界状态然后转发给客户端
			- 每个客户端根据这个世界状态进行差异插值

		- 纯状态同步

			- 逻辑在服务器
			- 转发

				- 转发的是输入被处理后的世界状态
				- 各个客户端收到的是定制化的数据

	- 帧同步

		- 转发校验

			- 缺点：等待全部客户端输入完成，造成延时
			- 将全部客户端的输入转发给每个客户端

		- 逻辑在客户端

- 其他

	- 流畅

		- 分帧执行，算法优化

			- 小心规划每一个函数

				- 每一帧的逻辑、渲染等耗时不能高于33MS

			- 稳定在30帧

		- 网络传输波动延迟

			- 固定延迟

				- 缺点：所有玩家固定延迟

			- 逻辑表现分离

				- 表现端AI预测

	- 断线重连

		- 断线

			- 心跳包
			- 逻辑帧停止，表现帧停止预测

		- 重连

			- 最新现场数据快速重连
			- 断线之后的数据，客户端加速播放

		- 追帧重回

			- 网络快照

	- 丢包重传

		- 原因

			- 发送端数据堆积

				- 降低发送频率

			- 数据过大

				- 网络模型自动有优化粘包分包

			- 接收端数据卡顿

				- buffer缓冲池
				- 多线程分次接受后合并

		- 粘包问题

			- TCP对过小的数据包做优化

				- 消息弹窗

		- 注意

			- 丢包问题是不能解决的（网络不同），只能避免

		- 解决：网络框架

			- ACK确认

				- 丢包号

			- 粘包

				- 自定义通信协议

					- 服务号
					- 命令号
					- 用户标识
					- 数据体协议

			- 冗余发送
			- 心跳包/RTO 重传超时时间

	- 数据协议

		- json

			- 原理

				- 明文
				- 基于文本格式

					- 整型、浮点数更占空间更耗时
					- 基于字符串的tag匹配

			- 缺点

				- 以下几种情况性能最差

					- 跳过非常长的字符串
					- 编解码double字段
					- 解码整数

		- XML
		- protobuf

			- 优势

				- 压缩性好
				- 序列化与反序列化快
				- 传输速度快

			- 缺点

				- 性能依靠语言与解析库的实现

			- 原理

				- 二进制、结构化
				- 基于数字的tag
				- 正文前有长度标记

	- 逻辑不同步问题

		- 随机数污染
		- 浮点精度
		- 逻辑顺序执行

			- 某些插件里的不稳定排序
			- List/Dict Sort()不稳定排序
			- 数据包顺序

				- 网络接收数据的先后顺序不一致的不同步
				- ACK自增编号

					- 对每一个发出的消息做一个自增的编号

		- 存储一致性

			- 多个容器引用同一对象

### AI

- 实践

	- 状态机
	- 行为树

- 预览

	- ml-agents

		- pyTorch

### 实践方案

- 大地形渲染方案

	- 模型：面数更少

		- LOD
		- Amplify Impostors

	- 贴图

		- minmap
		- Amplify Texture

	- 剔除

		- 遮挡
		- 视锥体

	- 网格合并
	- GPU计算

		- IOC

			- 它的思想就是第一步先做一个初略的遮挡裁剪列表，而后在此基础上再根据视线距离或者射线检测做进一步的细化裁剪操作

	- 多线程地图加载

- 大批量物体动画方案

	- DOTS
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

	- 待解决问题

		- 阴影渲染

- 碰撞穿模问题

	- 逻辑判断：判断上一帧与下一帧之间的碰撞路线
	- e.g. 子弹以极快速度射入射出一个碰撞体

- 抖动问题

	- e.g.

		- UI抖动
		- 动画抖动

	- 浮点数精度问题

- 地形接缝方案
- 手机发烫问题排查

	- 多相机
	- AA
	- 帧率
	- drawcall

- 困难与解决

	- 原生

		- 多进程
		- 屏幕正方向

	- 自定义坐标系

		- 高度的处理
		 
	- 动态加载环境光
	    - RenderSettings.skybox = clip;
	      DynamicGI.UpdateEnvironment();


## Unreal

### Unreal Engine 5 C++ Developer:Learn C++ & Make Viedeo Games | Udemy

- Welcome
    - [Intro & setup](./ue5/ue5-Intro-and%20Setup.md)
    - [Viewport](./ue5/ue5-editor-navigate-viewport.md)
    - [Actor](./ue5/ue5-blueprint-actor.md)
	- [help us to help you](./ue5/ue5-FAQ.md)

- Warehouse Wreckage
	- [project setting](./ue5/ue5-editor-setting-project.md)
	- [Blueprint Event Graph](./ue5/ue5-blueprint-event-graph.md)
	- [Physics Simulation](./ue5/ue5-physics-base.md)
	- [Adding an Impulse](./ue5/ue5-physics-force.md)
	- [Blueprint Classes and Instances](./ue5/ue5-blueprint-class.md)
    - [Transform](./ue5/ue5-transformation.md)
	- [Import Assets](./ue5/ue5-editor-import-assets.md)
	- [Materials and Lighting](./ue5/ue5-render-material-and-light.md)
	- [Actor Component](./ue5/ue5-component-base.md)
	- [Collision Meshes](./ue5/ue5-physics-collision.md)
	- [Variables](./ue5/ue5-blueprint-variable.md)
	- [Booleans and Branches](./ue5/ue5-blueprint-branch.md)
	- [Functions](./ue5/ue5-blueprint-function.md)
    - [Level](./ue5/ue5-blueprint-level.md)

- Obstacle Assault
