---
title: Game Develop
layout: doc
permalink: /gamedev/
---


# GamePlay

## Unity

### 性能优化

- 渲染

	- drawcall

		- [Batcher](./u3d-batch.md)
		- [UGUI](./u3d-batch-ugui.md)



							

		- 计算

			- 计算量

				- 复杂数学

					- 开方

				- 顶点函数-计算
				- 向量计算更加复杂

					- 尝试使用sqrMagnitude（即magnitude的平方）替代magnitude，减少开平方操作

			- 计算精度

				- 当使用CG / HLSL编写着色器时，存在三种基本的数字类型：float(32bits)，half(16bits)和fixed(11bits)

					- 对于世界空间位置和纹理坐标，使用float精度。
					- 对于其他一切（矢量，HDR颜色等），首先使用half精度，必要时增加精度。
					- 对于纹理数据的非常简单的操作，使用fixed精度。

		- model->mesh

			- 合并与裁剪

		- 其他

			- 字符图集
			- 特效清理

		- lightmap

			- 原理

				- uv2

			- 烘焙

	- overdraw

		- 原理

			- earlyZ

				- 硬件

			- preZ

		- 粒子发射器

			- 数量
			- 发射模型的复杂度
			- Particle System

				- lod
				- Scaling Mode
				- Max Particles
				- 避免Noise
				- speed <-> num

		- 透明问题

			- AlphaBlend

				- 堆叠

			- 透明裁剪

				- 不超过1个量级

					- 10倍

				- GPU对顶点的敏感度没有drawcall高

	- 带宽

		- model

			- lod

				- Fade Mode

			- 复杂度

				- 顶点数
				- 边界平滑

			- mesh collider

		- texture

			- minmap
			- 压缩格式

				- ETC
				- HEVC

			- 制作

				- 
				- 正方形纹理
				- 通道

		- material

			- shared

		- 程序化

- 脚本

	- UI

		- 动静分离

			- 一个元素发生改变同一个Canvas Renderer重新计算所有元素

		- 关闭不需要的设置

			- 射线检测

	- GC

		- 方法

			- LINQ

				- GC消耗
				- 多线程存储一致性
				- 原理

					- 复制原数据到开辟新内存空间进行SQL操作
					- 不改变原容器内存储

			- 临时变量

				- String

			- IDispose
			- 弱引用

		- 内存泄漏

			- 由于“存在该释放却没有释放的错误引用”，导致回收机制认为目标对象不是“垃圾”，以至于不能被回收

		- 对象池
		- 遮挡剔除
		- 精灵图集
		- 其他

			- foreach

				- 已被优化

	- 降低代价

		- Unity Update

			- GetComponment
			- Transform

				- Find
				- position

			- Camera.main
			- 固定增量时间
			- 空的事件方法
			- 空的生命周期

		- 循环
		- 异步加载

			- 协程
			- Async

				- 移动端禁止
				- 原理：多线程

			- 内容

				- Resources
				- Assetbundle

		- 变量类型所占内存

			- 数据类型与精度

- 分析工具

	- unity

		- Status

			- 参数

				- Audio
				- Graphics

					- CPU

						- main
						- render therad

					- batches

						- 批次数
						- Saved by batching

							- 被合批的物体数

					- Tris

						- 面数

					- Verts

						- 顶点数

					- Screen

						- 屏幕分辨率及显存

					- SetPassCall

						- 一次完整的渲染流程

					- Shadow Caster

						- 阴影开销

					- Visible skin mesh

						- 可见蒙皮网格

					- Animation

						- 动画组件数
						- 采样

							- 每一帧动画采样
							- 计算顶点位置

				- Network

		- Profiler

			- 追踪

				- Profiler.BeginSample()
Profiler.EndSample()

			- theory

				- 开销

					- 函数开销=调用一次开销*调用次数

						- 调用一次开销=调用其他函数开销+自身开销

							- Self：自身开销

						- call：调用次数

					- 优化

						- 优化热点：total高
						- 优化点

							- 调用时间
							- 调用次数

			- 面板

				- CPU Usage
				- Rendering

					- GPU Usage

			- 参数

				- OverView

					- WaitForTargetFPS

						- 绘制休眠时间=GPU绘制能力-绘制占用

					- Camera.Render
					- Overhead

						- 位置开销

							- 引擎没能统计

					- Animation.Update

						- 动画采样消耗

					- BehaviorUpdate

						- 脚本开销

					- GUI.Repaint

						- OnGUI开销

					- Canvas.RenderOverlat

						- UGUI开销

		- Profiler Analysis
		- Frame Debugger

	- Unreal

### CPU

- 实践

	- Unity

		- 生命周期

			- 本质：委托异步回调
			- e.g.

				- B:SetActive(false)
A:Awake(){
  B:Start();
}

		- 组件

			- UI

				- TextMeshPro

					- Text

						- SDF

							- shader

						- bitmap

					- Sprite Asset

						- 资源处理
						- 使用：<sprite=n>

					- Outline
					- Underlay
					- 优点

						- 图文混排
						- 合并drawcall

					- 缺点

						- 所有TMP默认共用材质
						- 堆内存消耗

				- 锚点

					- 实现原理

						- 数据结构

				- Canvas
				- UI隐显方式

					- Setactive

						- GC.Alloc

					- Transform
					- Layer
					- CanvasGroup

						- 不触发rebuild隐藏显示Pannel
						- 原理：子节点mesh顶点色与alpha相乘
						- 真正切到0时会有Batch，但是切到0.000000001时不会有

				- 渲染原理

					- rebatch

						- mesh

					- rebuild

						- material
						- layout

				- 优化UGUI

					- List刷新缓存
					- 删除不必要节点

			- Camera
			- Transform

				- 四元数和欧拉角

					- 万向节死锁
					- 定义域

						- 四元数不会超过180度

					- 存储空间

				- 结构：矩阵

					- 4*4矩阵

						- 1 0 0 x
0 1 0 y
0 0 1 z
 1 1 1 1

					- 位置

						- 03，13，23

		- Time

			- timeScale
			- unscaledTime

		- 物理

			- 碰撞检测

				- 第一阶段，broad phase 快速找出潜在的碰撞物体对列表，不在这个列表里的是绝对没可能碰撞的。broad phase确定了一批需要进一步检查的物体对。

					- broad phase其中有一个简单算法叫sweep and prune(SAP)，本质上是利用了排序算法。第一步是初始化排序列表，列表中的元素是包围盒，可以用任意排序算法完成，例如快排；之后的排序就不是用快排了，而是用冒泡排序，为什么用冒泡排序更好呢？是因为一个默认的前提：物体的运动有时间相关性（temporal coherence），即当前帧和下一帧的位置是相近的，所以在冒泡排序过程中，发生的位置交换预期都很靠近。

				- 第二阶段，narrow phase 准确找出发生碰撞的物体对列表。因为上一个阶段的部分物体对实际上是没有碰撞的，需要在这个阶段剔除。

		- Editor

			- Editor生命周期

				- OnEnable
				- OnFucus
				- OnInspectorUpdate
				- OnHierachyChange
				- OnProjectChange
				- OnGUI
				- OnLastFocus
				- OnDisable
				- OnDestroy

			- Drawer
			- 注解

				- 原理

					- 反射

				- 序列化与反序列化

		- 插件

			- LogViewer
			- EasyTouch
			- DOTween
			- Spine
			- FGUI

				- 优点

					- 开发效率

						- 美术优化
						- 方便拼界面

					- 减少消耗

						- 内存
						- GC

							- 动态改变无GC
							- 支持

								- 透明
								- 位移
								- 旋转

							- 不支持

								- 文字图片改变

						- UI Batch->reconsturct

							- 原理

								- 动态后期优化
								- 不需要动静分离

					- 自带缓存
					- 自带图集
					- 跨平台

				- 缺点

			- Cinemachine
			- Odin

				- Attribute

					- Simple

						- 功能

							- FilePath
							- Button

								- ButtonSizes
								- GUIColor

							- ShowInInspector/HideInInspector
							- PreviewField
							- HideLabel
							- LabelText
							- progressbar

						- 辅助

							- Required
							- AssetsOnly
							- PropertyOrder
							- ListDrawerSettings

								- CustomAddFunction 
								- CustomRemoveIndexFunction 

					- Group

						- HorizontalGroup
						- VerticalGroup
						- TabGroup(group, name)
						- TableList

							- TableColumnWidth

					- Meta

						- ValidateInput( FuncName )
						- OnValueChanged( FuncName )
						- InfoBox( Msg, FuncName)

					- Expression

						- 功能

							- InfoBox
							- ShowIf

						- 特性

							- @
							- $value
							- #

					- State

						- OnStateUpdate
						- PropertyRange
						- custom states

							- InspectorProperty.State.Get()
							- InspectorProperty.State.Set() 

					- Space

						- Space
						- PropertySpace

				- OdinEditorWindow

					- Create

						- MenuItem
						- private static void OpenWindow()

							-         GetWindow&lt;MyCustomEditorWindow&gt;().Show();
							- GetWindow<OdinEditorClassName>().Show();

					- Attribute

						- EnumToggleButtons
						- FolderPath

							- RequireExistingPath 

						- InlineEditor

					- Override Function

						- Initialize()
						- GetTarget()
						- BuildMenuTree()

							- Attribute

								- tree.Selection.SupportsMultiSelect
								- tree.DefaultMenuStyle

							- Func

								- Add(name, object)

									- object

										- GeneralDrawerConfig.Instance

								- AddAllAssetsAtPath(name, path, typeof(ScriptableObject))
								- EnumerateTree().AddThumbnailIcons();

				- Serializable

		- 协程

			- Unity线程
			- 协程

		- ScriptableObject
		- DOTS

			- ECS
			- job manager
			- burst
			- mathematics库
			- 其他

				- DOTS

					- 基础

						- HPC#，Hyper C#

							- GC

								- 可以暂停
								- IL2CPP

									- 模拟.Net GC
									- 效率低于C++

							- NativeArray<T>

								- 在C#层分配C++对象
								- 主动释放

									- 不需要C# GC

								- 只用于值类型（float,int,uint,short,bool...），enums，structs，和普通类型指针
								- Dispose()
								- 内存别名问题

									- NativeArray禁止了内存别名

										- 不允许两个变量名执行同一地址
										- 禁止引用

									- 数据存储一致性

										- 发生拷贝时直接在自身空间做修改
										- 改变任意变量不影响其他变量

											- 引用类型则不然，如string类型

						- Unity.Mathematics数学库

							- 直接映射到硬件SIMD寄存器

								- 原本cpu一个一个计算
								- 现在可以一次性计算
								- 原本Unity Math类不支持

					- Job System

						- theory

							- 高效运行多线程代码
							- before JobSystem

								- unity内部多线程，对外主线程
								- C#多线程只支持处理数据

							- 利用多核

						- Script

							- IJob

								- struct Job:IJob{}
								- var job=new Job()
								- JobHandle handle=job.Schedule();
handle.Complete();

							- IJobParallelFor

								- 完全并行
								- struct Job:IJobParallelFor{}
								- 数据加锁

									- ReadOnly
									- handle.Complete()

										- 等待job完成
										- 多线程数据存储

					- ECS

						- e.g.

							- Hyber render

						- 设计模式

							- 继承模式
							- 组合模式

								- ECS

						- Unity（before ECS）问题

							- 脚本数据在内存中不连续

								- 影响Cache命中率

							- 脚本中没必要的数据被提供了

								- Transform包括太多数据，然而使用的只有几个

							- 数据耦合

								- 多个脚本调用同一GO
								- 脚本是引用类型

									- 产生GC

								- 脚本已经是很重量级的产物

									- 挂脚本就会额外产生耗时0.01s
									- 回调众多20+

								- 热更新不友好

						- theory

							- ECS

								- entity

									- a key
									- bind lots of component

										- 轻量级
										- Cache友好

											- 相同组件排列在连续内存，增大Cache命中

												- Archetyoe

									- entity≠GO
									- Archetyoe

										- made of chunks

											- 容器

												- 16KB

											- 不够再申请

										- 内存连续性
										- Cache命中

											- 每个实体的相同组件在内存中连续

								- component

									- :ICompionentData

										- 实质：struct数据存储

											- component≠monobeihavior
											- 无GC
											- Fuction无作用

									- ISharedCompnentData

										- 比较

											- IEquatable<MyCompnet>

										- 结构体内容完全相同
										- e.g.

											- SharedMesh

								- system

									- 只关心Component
									- 查找Component快

										- 子主题 1

									- Script

										- EntityQuery query=GetEntityQuery(typeof(COMPONENT1),typeof(COMPONENT2))
										- var com1=query.ToComponetDataArrat<COMPONENT1>(Allocator.Temp)

							- World

								- 组成

									- EntityManager
									- ComponentSystem

										- 主线程
										- JobComponentSystem

											- 同步点

												- 实体创建\销毁\组件添加删除
												- 主线程卡顿

										- IJobForEach<T1,T2>

									- Archtype

								- create

									- default
									- new world()

								- 多world间并行不互通

							- 默认编写高性能代码

					- Burst

						- 生成高度优化的本地代码
						- 编译器

							- 基础

								- LLVM

									- IR抽象语言
									- 支持多语言
									- 开源

								- 后端编译

							- 原理

								- 源代码-》全段-》优化器-》后端-》机器码

						- 缺点

							- 只支持值类型

								- LLVM对C# GC支持极差

						- Script

							- [BurstCompile]
struct job...

					- how to

						- entity->prefab

							- EntityManager.CreateEntity()

						- prefab->entity

							- proxy
							- noproxy

								- component

									- GenerateAuthoringComponent

								- System
								- Other

									- :IDeclareReferencedPrefabs,IConvertGameObjectToEntity

					- Debug

						- Entity Debugger

					- export to ecs

						- Hybrid

							- scene批量转换ECS工具
							- 默认不支持Lightmap，需要自定义实现
							- SubScene

								- World.GetOrCreateSystem<SceneSystem>()
								- 流式加载

									- LoadSceneAsync()
									- UnLoadScene()

						- GameObjectConversionUtility.ConvertGameObjectHierachy()

							- GO->ECS
							- 只支持部分

					- 渲染

						- theory

							- Job准备数据

						- 方法

							- GPU Instancing
							- CommandBuffer
							- BatchRendererGroup

								- 强制镜头裁剪Job
								- 需要提供每个渲染物体的包围盒区域

									- 镜头裁剪相关

								- 没有1023数量限制

									- 内部调用自动Graphics.DrawMeshInstanced （前提：开启GPU In试探此难关）

						- 问题

							- 裁剪

								- 需要自定义

							- Update每帧强制调用调用产生额外开销

								- Unity对物体的一些优化没有了：如不发生改变的物体
								- CommandBuffer

							- 贴图烘培

								- https://www.bilibili.com/video/BV18J411t7G8/?spm_id_from=333.788.recommend_more_video.5

							- 骨骼动画

								- 原理

									- GPU蒙皮

										- CPU拿到GPU蒙皮挂点
										- OpenGL ES3.0 API Transform Feedback 回传信息到CPU
										- Job实现（多线程）

									- animation instancing

										- 每帧骨骼及蒙皮信息烘焙到一张图
										- Shader uv动画
										- 问题

											- 挂点信息

												- 解决：editor编写脚本记录每帧挂点

										- 隐患

											- GPU开销
											- 内存开销
											- 设备兼容

												- 需要支持GPU动画Fallback CPU动画

								- Job动画

									- AnimationScriptPlayable

										- 不需要AnimationController

						- 优化

							- Drawcall划分
							- 原做法和DOTS混合使用

								- 原做法复制静态物体
								- 原做法转DOTS后MonoComponent会展城IComponent

									- 原做法转换后的组件原方法均无法使用

						- SHADER

		- Input

			- InputManager
			- InputSystem

		- 资源管理

			- Resources

				- 本地
				- 发布后不能修改

			- AssetBundle/Addresable

				- 内存管理

					- 释放时机

						- 引用计数
						- 非即时

							- 应避免资产流失

					- 释放方法

						- release instance
						- release handle
						- Resource.UnloadunUsedAsset

					- 内存开销

						- 加载缓存
						- 类型树 Type Trees

							- 同一个bundle保持资源类型一致
							- 首选简单的数据类型
							- 关闭类型树（unrecommend）

								- BuildAssetBundleOptions.DisableWriteTypeTree
								- 加载旧版本bundle可能会序列化错误

						- 内容表 Table of contents

							- 资源名称映射

						- 预先加载表 Preload table

							- 资源依赖

					- 句柄管理

						- 组

				- 资源加载

					- 依赖加载
					- 异步加载
					- 同步等待

						- WaitForCompletion()
						- 实质：while循环

					- 清理缓存

				- 打包

					- 场景文件及涉及的资源单独打包

				- Catalog
				- URL转换
				- AB与AA区别

					- AA自动管理依赖
					- AA增加Label属性
					- AA增加组模式
					- AA不需要初始化下载完所有资源

			- AssetBundle

				- .manifest

					- .manifest
					- 校验码

				- 原理

					- 当AssetBundle 解压加载到内存之后，我们可以通过WWW.assetbundle属性获得AssetBundle对象（上图的粉色框部分）来得到各个Assets，并对这些Assets进行加载或者实例化操作
					- unity会将AssetBundle中的数据流转变成unity可识别的信息类型。加载完成之后，我们就可以对其进行更多操作了

				- 打包

					- 冗余
					- 原生资源
					- 设置

						- 平台
						- 压缩方式

							- LZMA

								- 压缩的包更小，但是加载时间更长
								- 用之前需要整体解压。一旦被解压，这个包会使用LZ4重新压缩

							- LZ4

								- 以加载指定资源而不用解压全部

							- 不压缩

								- 包大，加载快

						- 增量打包

							- 新文件
							- 老文件更新

					- 打包方案

						- 分组

							- 将需要同时加载的资源放在同一个包里

						- 场景文件中会单独打包

							- 其中有预制体又会被打包一次

				- 加载

					- 原理

						- Manifest文件

							- 得到某个包的依赖

						- 依赖加载

					- AB包

						- WWW  /  UnityWebRequest
						- AssetBundle.LoadFromFile

							- AssetBundle.LoadFromFile

				- 卸载

					- 方案

						- 引用计数管理

							- 避免重复对象

						- 弱引用

					- Asset

						- Resources.UnloadAsset(obj)

					- AssetBundle

						- Unload(bool)

							- true

								- 卸载AB包及场景内正在使用

							- false

								- 只卸载AB包，切断资源引用
								- 再次加载产生重复对象

						- Resources.UnloadUnusedAssets()

							- 没有额外附加特性地加载一个场景。这将消除当前场景的所有对象，并自动调用 Resources.UnloadUnusedAssets。
							- 该接口作用于整个系统

					- 实例化对象

						- Destroy

							- unity会将真正的删除操作延后到一个合适的时机统一进行处理，但会在渲染之前

						- DestroyImmediately

				- 平台差异

					- PC
					- Android
					- IOS

			- Addresable

				- 基于assetbundle
				- 更方便地管理

		- 热更新

			- 流程

				- 打包时放到StreamAssetPath
				- 第一次加载时解压到PersistPath
				- 本地版本号与服务器做对比
				- Hash判断具体AB包需要更新

			- 框架

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

