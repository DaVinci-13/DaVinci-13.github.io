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
		        - [Batcher](./render-batch.md): dynamic、static、GPU Instancing、SRP Batcher
		        - 减少[复杂计算](./render-shader.md)
		        - 模型网格的裁减与合并
			    - 字符图集
			    - 特效清理
		        - [lightmap](./u3d-lightmap.md)
		        
	        - overdraw
			    - [earlyZ & preZ](./render-earlyZ-and-preZ.md)
		        - [Partical System](./u3d-ParticalSystem.md)
		        - [AlphaClip & AlphaBlend](./render-AlphaClip-and-AlphaBlend.md)

	        - 带宽

		        - [model](./art-Modeling.md)
		            - 降低复杂度
			        - [lod](./u3d-lod.md)

		        - [texture](./art-texture.md)
		            - 程序化纹理 
		        - SharedMaterial 共享材质

        - 脚本

	        - [UGUI Batch](./render-ugui.md)
	        - [GC](./clr-gc.md)
	        - [u3d优化](./u3d-optimize.md)

    - 分析工具
	    - [Stats](./u3d-stats.md)
        - [Profiler](./u3d-profiler.md)			
	    - Profiler Analysis
	    - Frame Debugger

    - Unity  生命周期(本质：委托异步回调)
    
	- Component
	    - [UI](./u3d-ugui.md)
		    - [TextMeshPro](./u3d-textmeshpro.md)
	    - Camera
	    - [Transform](./render-transformation.md)
	    - 【Time】

		- Input
			- InputManager
			- InputSystem

	- ScriptableObject
	
    - [UnityEditor](./u3d-editor-scripting.md)

    - 插件
	    - LogViewer
	    - EasyTouch
	    - DOTween
    	- Spine
	    - [FGUI](./u3d-fgui.md)
	    - Cinemachine
    	- [Odin](./u3d-odin.md)
	
	- [DOTS](./u3d-dots.md)
	
	- 资源管理
	    - [Resources](./u3d-resources.md)
	    - [AssetBundle & Addresable](./u3d-addresable.md)

    - 物理

			- 碰撞检测

				- 第一阶段，broad phase 快速找出潜在的碰撞物体对列表，不在这个列表里的是绝对没可能碰撞的。broad phase确定了一批需要进一步检查的物体对。

					- broad phase其中有一个简单算法叫sweep and prune(SAP)，本质上是利用了排序算法。第一步是初始化排序列表，列表中的元素是包围盒，可以用任意排序算法完成，例如快排；之后的排序就不是用快排了，而是用冒泡排序，为什么用冒泡排序更好呢？是因为一个默认的前提：物体的运动有时间相关性（temporal coherence），即当前帧和下一帧的位置是相近的，所以在冒泡排序过程中，发生的位置交换预期都很靠近。

				- 第二阶段，narrow phase 准确找出发生碰撞的物体对列表。因为上一个阶段的部分物体对实际上是没有碰撞的，需要在这个阶段剔除。

    - 异步
	    - [C#线程](./cs-thread.md)
	    - [C#异步](./cs-async.md)
	    - [Unity协程](./u3d-corotinue.md)

		
    - 热更新

			- 流程

				- 打包时放到StreamAssetPath
				- 第一次加载时解压到PersistPath
				- 本地版本号与服务器做对比
				- Hash判断具体AB包需要更新

			- 脚本热更新方案

				- C#

					- ILRuntime

						- 优势

							- 无缝访问C#

								- 跨域继承
								- 泛型支持
								- 无需抽象API

							- 执行效率

								- L#*10~20
								- CLR绑定=sLua*2

							- 调试插件
							- vs. Lua

								- Lua

									- 成熟
									- 历史原因
									- 熟悉Lua

						- 步骤

							- 加载dll

								- 读取streamingAsset/*.dll到内存
								- appdomain.LoadAssembly()
主工程读取dll到解释器

							- 初始化CLR
							- OnHotFixLoaded()执行逻辑处理

						- 结构

							- Unity主工程

								- 不能热更
								- MonoBehavior
								- 加载dll

							- HotFix_Project.dll

								- 热更工程
								- Unity将"~"结尾的文件与文件夹在Editor下隐藏

						- 概念

							- 跨域

								- 委托

									- 额外适配器/转换器

								- 继承

									- 继承适配器

										- 主工程
										- 注册

								- 原理

									- appdomain 程序域
									- 反射

							- 反射转换

								- 类型映射

							- 高性能

								- CLR重定向
								- CLR绑定

						- 原理

							- Mono.Cecil
							- IL托管栈

								- unsafe
								- 非托管内存

						- 性能优化

							- Release模式测试
							- 关闭Development Build
							- 避免GC

								- 取代默认反射

									- CLR绑定
									- InvocationContext

								- 重新实现基于IL托管栈的值类型绑定
								- 避免频繁调用可变参数列表

									- 可变参数列表原理：new 数组

						- 解决方案

							- 不依赖于MonoBehavior的框架
							- 自动化CLR绑定代码生成
							- Addressable

					- 原理

						- dll

					- hybridCLR

				- lua

					- 原理

						- lua运行时才编译的特性

							- DOT

						- lua文件也可以被看成是一种资源文件
						- 虚拟机

							- 虚拟栈
							- 虚拟机指借助软件系统对物理机器指令执行进行的一种模拟
							- lua脚本并不是直接被Lua解释器解释执行，而是类似Java语言那样，先由Lua编译器编译为字节码，然后再交给Lua虚拟机执行

					- xlua

						- 交互

							- [Hotfix]

								- 然后在所有可能出现问题的类上打上HOTFIX的标签，在所有Lua调用的方法上打上LuaCallCSharp标签，在所有CSharp调用Lua的方法上打上CSharpCallLua

									- [CSharpCallLua] 

										- 映射Lua中的变量函数等成C#类型
										- 在C#中对应的Delegate或Interface添加该标签

									- [LuaCallCSharp] 

										- 适配器代码

											- lua虚拟栈

										- 反射

								- xlua.hotfix(CS.类名,‘方法名’,function(self)
具体实现的方法体
end) 

							- CS.UnityEngine、CS.类名.方法
							- self:方法名() 或者 self.方法名(self) 
							- CustomCall call=XLuaMgr.GetInstance().Global.Get<CustomCall>("testFun1");
call();

						- 优势

							- 通过[hotfix]对c#中的代码进行修改

								- 可能出现bug或者后期需要更新逻辑
								- 给这个类加上[HotFix]标签，并在方法上打上[LuaCallCSharp]标签，那么当需要更新这个方法时，只需在lua脚本中重新实现这个方法

							- GC性能提升

					- tolua

		- 打包

	- 原生交互

		- Android

			- unity

				- 打包

					- Unity做好项目之后导出为Android Studio项目，导入到Android Studio中进行之后的功能开发
					- Android Sutido做好项目导出jar或aar包，导入到Unity中作为Unity的插件使用，最后由Unity打包APK

				- Unity调Andoird：
// 获得位于com.unity3d.player包下的UnityPlayer类，固定写法。
        AndroidJavaClass jc = new AndroidJavaClass("com.unity3d.player.UnityPlayer");   // 参数是包名+类名
        // 获得jc所代表的类里的currentActivity对象，固定写法。这是Unity提供的classes.jar中的功能，可通过currentActivity获取到安卓端代表MainActivty的对象。
        AndroidJavaObject jo = jc.GetStatic<AndroidJavaObject>("currentActivity");
        // 调用MainActivty中的自定义方法。
        text.text = jo.Call<int>("add", 1, 2).ToString();

					- 1、打开Android Studio新建一个项目，新建一个模块（Module），取名UnityAndroidLibrary。注意选择最小SDK16，因为Unity最小支持的是16。
					- 2、在该模块（ProjectName/UnityAndroidLibrary/src/main/java/packageName/）下新建一个Empty Activity。创建时勾上Launcher Activity。
					- 3、删除跟该界面一同生成的activity_main.xml布局文件（因为之后布局归Unity管理），同时删除该模块MainActivity中onCreate()里调用setContentView()方法。
					- 4、进入Unity的安装目录（如D:\Unity 5.4.3f1\Editor\Data\PlaybackEngines\AndroidPlayer\Variations\mono\Release\Classes下）复制classes.jar文件，粘贴到该模块UnityAndroidLibrary/libs目录下。右键该jar选择Add as Library，选Add to Module UnityAndroidLibrary。
					- 5、打开UnityAndroidLibrary模块的AndroidManifest.xml清单文件，该文件会覆盖掉Unity的一些设置，修改如下。（从默认的app模块中的清单文件拷贝过来，把报错的地方去掉即可。记得加后面的meta-data节点）
					- 6、回到模块的MainActivity，修改该类继承自UnityPlayerActivity。在该类中添加自定义的方法，用于给Unity调用
					- 7、在AS中Project目录选中unityandroidlibrary，在Build菜单下选Make Module ‘unityandroidlibrary’单独编译这个模块。
					- 8、在unityandroidlibrary/build/intermediates/bundles/debug目录右键Show in Explorer。删除debug/libs/classes.jar（等同于刚从Unity那边拷过来的内容），把debug/classes.jar拖到debug/libs中（这个是包含了刚新增的扩展方法的）。把libs和res这两个文件夹备份（如复制到桌面）。　
					- 9、在unityandroidlibrary/build/intermediates/manifests/full/debug/AndroidManifest.xml右键Show in Explorer，也把这个清单文件复制出来（如复制到桌面）。打开在桌面的副本，修改package包名为在Unity中想要的包名，如包名最后一段改为unityandroidtest（注意包名要全部小写）。
					- 10、打开Unity，创建一个工程UnityAndroidTest，Build Settings切换为安卓平台，Player Settings中修改包名，包名同上一步的一致（先调平台再调包名）。在Assets下新建文件夹Plugins/Android（名字固定的，小心别漏了s），将上两步得到的三个文件拖到该文件夹中。
					- 11、新建一个C#脚本，VS打开编辑如下。把该脚本挂到任一场景中的游戏对象上（如Main Camera)。
					- 12、最后一步，连上真机并打开USB调试，Build & Run，路径选择桌面。此时会把APK输出到桌面并安装到真机上运行，即可看到调用结果。下图是我用AS的安卓模拟器（AVD）运行的效果。注意了，要打包发布出来用，直接在Unity编辑器点运行会报错，但打包出来安卓机运行没有问题的。

				- Andoird调Unity：
UnityPlayer.UnitySendMessage("Main Camera", "ChangeColor", "");
				- 路径

					- path

						- Resources
						- streamingAssetsPath

							- 移动只读

						- persistDataPath

							- 可读可写
							- 在Android上的位置是根据Project Setting里设置的Write Access路径
							- 在IOS上是应用程序的沙盒

						- dataPath

							- 移动无用

						- temproryCachePath
						- consoleLogPath

					- load

						- file

							- 无前缀

						- www

							- PC

								- file://+path

							- IPhone

								- file://+path

							- Android

								- 无前缀
								- 默认为有 "jar:file:///" 

		- IOS

- 原理

### Shading

- 图形学

	- 光栅化
	- 几何

		- MVP变换
		- 向量计算

	- 光线追踪

		- PBR

			- 原理

				- 微表面理论
				- 能量守恒
				- BRDF

			- BRDF

				- NDF
				- GO
				- Fresnel

			- 贴图

				- BaseTex
				- Normal
				- Metallic/Speculiar
				- AO
				- Ambient
				- 环境色

	- 动画模拟

- 渲染理论

	- 渲染流水线

		- 应用阶段

			- 粗粒度剔除

				- 遮挡剔除
				- 视锥体剔除

			- 渲染设置
			- 准备数据

		- 几何阶段

			- Vertex Shader
			- Tesselation Shader
			- Geometry Shader
			- 视锥体裁剪
			- MVP

		- 光栅化阶段

			- 渲染三角形

				- 设置
				- 遍历

			- AA 抗锯齿

		- 片元处理 Fragment Shader

			- 三大测试

				- AlphaTest 裁剪测试
				- Stencil Test
				- Depth Test

			- 颜色混合

		- 后处理

	- 渲染管线

		- Forward
		- Deferred 延迟

			- 与场景模型复杂度无关
			- 解决大量关照渲染
			- 实质为后处理进行光照计算

	- 渲染技术

		- 体渲染

			- 云

		- 视差

			- 云
			- 冰

		- PBR
		- Stylized

			- 水
			- 火

		- 后处理

			- AA
			- Outline/Rim
			- Bloom

				- GaussBlur

			- Dof
			- AO

	- Gamma矫正
	- 算法

		- 高斯模糊
		- AA
		- AO

			- SSAO
			- HBAO

		- Dof
		- PBR

			- BRDF

- 实践

	- unity

		- 管线

			- build-in
			- urp

				- 只第一个pass起作用
				- 定制后处理插入点
				- SRP Batcher

			- hdrp

		- 路径

			- 前向
			- 延迟

		- Shader

			- MetaPass

				- 为光照映射和动态全局光照提取表面信息的Pass块

			- Shader变体

				- 类型

					- multi_complie
					- shader_feature

						- feature在打包（build）的时候不会把未使用的 variants 打进去， 因此应该使用shader_feature来声明那些material设置的关键词，全局代码使用的关键词最好用shader_compile来声明

				- [*]_local

					- 局部

						- 可用数量：64

					- 全局

						- 可用数量：200-

							- 总数(256)-Unity内部占用(60-)

				- #pragma multi_compile __ METHOD1

					- 该指令生成了两个着色器变体，一个未定义的“__”，和一个“METHOD1 ”，如此可以避免把两个关键字都用完

				- 计算

					- multi_compile A B C
multi_compile D E
6=3*2

				- C#调用

					- Shader.EnableKeyword：启用全局关键字
					- Shader.DisableKeyword：禁用全局关键字
					- CommandBuffer.EnableShaderKeyword：使用CommandBuffer来启用全局关键字
					- CommandBuffer.DisableShaderKeyword：使用CommandBuffer可以禁用全局关键字
					- Material.EnableKeyword：为常规着色器启用本地关键字

						- 若不存在，则创建全局关键字

					- Material.DisableKeyword：禁用常规着色器的本地关键字
					- ComputeShader.EnableKeyword：为计算着色器启用本地关键字
					- ComputeShader.DisableKeyword：禁用计算着色器的本地关键字

				- unity内置

					- 类型

						- multi_compile_fwdbase 编译PassType.ForwardBase所需的所有变体。这些变体处理不同的光照贴图类型，并且启用或禁用了主方向光的阴影。
						- multi_compile_fwdadd 编译PassType.ForwardAdd的变体。这将编译变体以处理定向，聚光或点光源类型，以及带有cookie纹理的变体。
						- multi_compile_fwdadd_fullshadows 与相同multi_compile_fwdadd，但还包括灯光具有实时阴影的功能。
						- multi_compile_fog 扩展为多种变体以处理不同的雾类型（关闭/线性/ exp / exp2）。

					- 跳过

						-  #pragma skip_variants

				- 其他

					- Graphics tiers and shader variants（图形层和着色器变体

						- Unity将检查GPU的功能，并确定其对应的图形层，我们可以为每一个图层创建一组着色器变体，并通过“#pragma hardware_tier_variants renderer（其中renderer是有效的渲染平台）” 设置不同的图形层 （此功能仅与内置渲染管线兼容）

							- d3dll

								- Direct3D 11/12

							- glcore

								- OpenGL 3.x/4.x

							- gles

								- OpenGL ES 2.0

							- gles3

								- OpenGL ES 3.x

							- metal

								- IOS/Mac

							- vulkan
							- d3dll_9x

								- Direct3D 11 9.x

							- xboxone
							- ps4
							- n3ds
							- wiiu

						- eg

							- #pragma hardware_tier_variants gles3

						- Unity还会为每个着色器生成三个着色器变体

							- UNITY_HARDWARE_TIER1  

								- //第一图形层（低）-对应于着色器定义UNITY_HARDWARE_TIER1。
								- //选择此级别的对象是：-不支持OpenGL ES 3的Android设备-iPhone 5、5C和更早的版本-iPod Touch第5代或更早版本-iPad 4或更早版本-iPad Mini第1代-台式机上的DirectX 9类硬件-HoloLens

							- UNITY_HARDWARE_TIER2

								- //第二个图形层（中）-对应于着色器定义UNITY_HARDWARE_TIER2。
								- //选择此等级的用户包括：-支持OpenGL ES 3.0+的Android设备-iPhone 5S及更高版本-iPod Touch第6代-iPad Air及更高版本-iPad Mini第2代及更高版本-Apple TV

							- UNITY_HARDWARE_TIER3

								- //第三图形层（高）-对应于着色器定义UNITY_HARDWARE_TIER3。
								- //选择此层可用于：-台式机上的OpenGL或DirectX 11+类硬件-Mac上的Metal

	- unreal

		- shader脚本

### 动画

- 通用

	- 挑战

		- 可交互

			- 动画状态机

		- 实时

			- 动画压缩

		- 真实感

			- Motion Matching

	- 动画类型

		- 序列帧动画

			- 2D
			- 仿3D

				- 各视角采样

			- e.g.

				- unity:Animation

		- 骨骼动画

			- 2D

				- 2D拆分

					- spine

				- live2D

					- 网格控制
					- 深度控制

			- 3D

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

		- 顶点动画

			- theory

				- 物理模拟
				- 动画烘焙
				- 离线

			- e.g.

				- unity：Skinned Mesh Renderer->Mesh Renderer

		- 表情动画

			- Morph Target Animation

				- theory

					- 顶点动画变体
					- 插值

				- e.g.

					- 捏脸

			- e.g

				- unity:BlendShape

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

- Intro & setup

	- install

		- https://www.bilibili.com/video/BV1be41137Kp/?p=13&spm_id_from=pageDriver

	- forum and support
	- Navigating the Viewport

		- interface

			- New Project
			- Viewport
			- Outliner
			- Content Browser
			- toolbat

				- Setting

					- Engine Scalability Setting

		- shortcut

			- mouse

				- right click

					- rotate all axis

				- left click

					- rotate in xz panel

				- mid scroll

					- move in xy panel

			- keyboard

				- wasdqe

			- ctrl+c & ctrl+v

				- copy

			- alt & drag

				- copy

	- Moving & placing Actors
	- C++ versus Blueprint

		- vs

			- Blueprint Strengths

				- Quick to change
				- Beginner friendly
				- Easy to discover
				- Tailor-made
				- Designer/artist friendly

			- C++ Strenths

				- More concise
				- Industry standard
				- High speed
				- Access all areas
				- Good for bigger projects

		- work together

	- help us to help you

		- Asking For Help
		- Good Questions

			- What have you tried?
			- What did you expect to happen?
			- What actually happen?
			- Be specific:exact error, screenshots, etc.

		- Useful Information To Include

			- Steps you're taken
			- Screenshots
			- Full Build logs
			- Editor Log
			- Your project

		- Log

			- Engine Log Window
			- project Directory->Saved->Logs

		- share

			- Engine Toolbar->File->Zip project

- Warehouse Wreckage

	- Intro
	- project setting

		- map

			- icon

				- with yellow line

		- level blueprint

	- Blueprint Event Graph

		- visual programming
		- glossary

			- Event Graph - The canvas for our Blueprint
			- Node - premade functionality
			- String - Programmer speak for text
			- Event - A "when" node
			- Pin - Sockets we can connect up
			- Input Pin - when to run this node
			- Output Pin - what to do after
			- Connection - Wires between pins

		- e.g.

			- BeginPlay(Event)->PrintString(Func)

	- Physics Simulation

		- Detail->physics

			- Simulation Physics
			- Enable Gravity
			- Mass

	- Objects and References

		- Objects
		- Glossary

			- Objects - Collections of data and functionality
			- Actors - Object that can go in a level
			- Component - Objects that can go on an actor
			- Reference - Where to find an object
			- Data Pin - The input or output data for a node
			- Excution Pins - When to run this node

		- e.g.

			- GetDisplayName
			- GetTheMass

	- Adding an Impulse

		- Content Sensitive

			- True means it filters down the nodes available to the ones that use the static mesh component object.

		- Force and Impulse

			- Force=Mass*Acceleration
			- Impulse=Mass*Velocity Change

		- Add Impulse(Component)

			- Impulse(vector3 value)
			- Vel Change(checkbox)

				- change nowtick speed

	- Blueprint Classes and Instances

		- Glossary

			- BP_Class

				- Detail->Convert ...

			- linked copy
			- instance

	- Spawning Actors

		- Glossary

			- Spawning

				- Creating an object while playing

			- Transform

				- Location, rotation and scale

			- Return pin

				- Output of a node

		- Hook Up The Impulse

			- Hook up the execution pins
			- "Add Impulse" should happen affter spawing
			- Hook up the data pins
			- What should we be adding the impulse to?

	- Data Types

		- Can't get a square peg in a round hole
		- Glossary

			- Integer
			- Float
			- String
			- Bool
			- Struct

				- An object that is usually small
				- e.g.

					- Transform

			- Objects

				- e.g.

					- Actors

						- Cube

					- Components

						- StaticMeshComponent

				- Collections of data and functionality

			- Data type

				- The "Shape" of your data

	- Pawns and Actor Location

		- Player Start (Pawn)
		- Get Player Pawn (Node)

	- Control Rotation

		- ActorRotation vs. ControlRotation

			- ActorRotation

				- belong to actor

			- ControlRotation

				- associate with inner camera
				- belong to controller

			- controller control actor

				- Pawn->Use Controller Rotation

	- Vector Addition & Multiplication

		- What Are Vectors?

			- Mathematically

				- Direction
				- Size(Magnitude)

			- Programmatically

				- 3 Floats
				- XYZ

		- Addition/Subtraction
		- Multiplication

	- Get Forward Actor
	- Import Assets

		- Windows
		- Mac

			- Content Browser-><select Assets or Folder><right click>->Migrate

	- Geometry Brushes (BSP)

		- Place Actors

			- Brush Type

				- substract

		- Set Default Map

			- Project Settings->Project->Maps&Modes

	- Materials and Lighting

		- Materials
		- Lighting

			- Light Source
			- Skylight

	- Actor Component

		- Parent and Child Actor

	- Collision Meshes

		- VIEW MODE

			- Locate: <Viewport> -> <Left-up Corner> -> VIEW MODE
			- modes

				- Lit
				- wireframe
				- Player Collision

		- Change Collider

			- Static Mesh Editor

				- toolbat->Collision->Remove Collision

		- problem

			- flying through

				- move too fast

	- Variables

		- Variables Are Like Boxes

			- Variables help us store, manipulate and refer to  information
			- Each variable

				- has a NAME
				- contains DATA
				- is of a particular TYPE

		- My Blueprint

			- Locate

				- Level Blueprint

					- Option->Window->My Blueprint

			- VARIABLES

				- function

					- Get
					- Set

			- subtract

				- Get the ammo value from variable
				- Subtract one from it
				- Store it back in the ammo variable
				- Print the result

	- Booleans and Branches

		- Glossary

			- Branch

				- Do something or do not, based on a bool

			- Booleans

				- What Is A Bool?

					- Bools are types that can store one of two values - true or false
					- They are often used with if statements to decide whether something happens or not
					- Certain nodes return bools

				- A yes or no data tyoe

			- Comparison

				- Less than, Greater than, Equal, etc.

	- Functions

		- commet block

			- hotkey

				- C

			- put some node into a block

		- What Are Functions?

			- Function execute blocks of blueprint that makes our game do thins.
			- Many node provided are functions.

				- It (node) has a little f symbol in the top left that stands for function

			- But we can create our own too.
			- They allow us to stay organised.
			- And reuse blocks of code.

		- How to

			- (Select some nodes)->(Right-click)->Convert to Function

		- Good Naming

			- Code is communiction.
			- Measure of code quality = WTHs / Minute
			- Functions should be bert
			- Talk to somebody else!

	- Return Types

		- Details

			- Outputs

				- DataNode

			- Inputs

				- DataNode

	- Pure Function

		- Side Effect

			- When a function has an observable effect

		- What Is A Pure Function

			- A Function with no side effects
			- Only return values

		- Make Function Pure

			- Select and set the checkbox
			- What happen to the execution flow

	- Member Fuctions

		- Glossary

			- Robecje Oriented Programming - Fuctions live with the data they manipulated.
			- Member functions - A function on a class, always called on an particular instance.
			- Self - A node available in member functions, always points to the current instance.

	- Loading Levels & Delay Nodes

		- Open Level

			- by Name

		- Get Current Level Name
		- Delay

	- Wrap-up and Recap

		- What We've Learnt

			- Blueprint Basics: nodes, pins
			- Programming basics: variables, strings, references, functions
			- Unreal basics: maps, actors, components, transforms, vectors
			- Object Oriented basics: objects/structs, classes, member functions.

- Obstacle Assault

	- Section Intro

		- Action Plan

			- 1. Create a project with our assets
			- 2. Install the tools we need for C++
			- 3. Learn same C++ basics
			- 4. Make a platform that moves
			- 5. Configure our moving platforms
			- 6. Send the platform back
			- 7. Rotating platforms.

		- What We Will Learn

			- Functions, Variables and Branches in C++
			- Creating a C++ Actor
			- C++ node structure
			- C++ Compilation and Live Coding
			- Linking Blueprint to C++
			- Setting our own custom character class.

