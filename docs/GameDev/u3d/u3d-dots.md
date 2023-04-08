---
layout: doc
title:  "DOTS - 学习1"
date:   2023-04-05 15:37:00 +0800
categories: Unity, dots, UI
---
# Unity DOTS

## Glossary
### 诞生原因
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

### 使用
导入 HybridRenderer

## ECS
组合模式
    
### Entity
1. Constitute
        - a key
		- bind lots of component
	        - 相同组件排列在连续内存，增大Cache命中
	    - 轻量级
2. entity->prefab
    ```csharp
    EntityManager.CreateEntity()
    ```
3. prefab->entity
- proxy
- noproxy
	- component
		- GenerateAuthoringComponent
	- System
	- Other
		- :IDeclareReferencedPrefabs,IConvertGameObjectToEntity
### Component
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
### System

- 只关心Component
- 查找Component快
	- 子主题 1
- Script
    ```csharp
	EntityQuery query=GetEntityQuery(typeof(COMPONENT1),typeof(COMPONENT2));
	var com1=query.ToComponetDataArrat<COMPONENT1>(Allocator.Temp);    
    ```

---
## job system
1. 优势
	- 高效运行多线程代码
	- before JobSystem
		- unity内部多线程，对外主线程
		- C#多线程只支持处理数据
	- 利用多核
1. 接口
	1. IJob

    ```csharp
    struct Job:IJob{
    };
    var job=new Job()
    JobHandle handle=job.Schedule();
    handle.Complete();
    ```  

    2. IJobParallelFor
    
    ```csharp
    struct Job:IJobParallelFor{
    };
    //等待job完成
    handle.Complete()
    ```
    - 优点
        - 完全并行
        - 数据加锁 ReadOnly
        - 多线程数据存储
---

## burst
1. 优点：
- 生成高度优化的本地代码
- 编译器
	- 基础
		- LLVM
			- IR抽象语言
			- 支持多语言
			- 开源
		- 后端编译
	- 原理
		- 源代码->全段->优化器->后端->机器码
2. 缺点:
	- 只支持值类型
	- LLVM对C# GC支持极差
3. e.g.
    ```csharp
    [BurstCompile]
    struct job{
    };
    ```
---

## mathematics库
原理：直接映射到硬件SIMD寄存器
- 原本cpu一个一个计算
- 现在可以一次性计算
- 原本Unity Math类不支持

---
## HPC#，Hyper C#

### GC
- 可以暂停
- IL2CPP
	- 模拟.Net GC
	- 效率低于C++
### NativeArray<T>
- 在C#层分配C++对象
- 主动释放
	- 不需要C# GC
- 只用于值类型（float,int,uint,hort,bool...），enums，structs，普通类型指针
- Dispose()
- 内存别名问题
	- NativeArray禁止了内存别名
		- 不允许两个变量名执行同一地址
		- 禁止引用
	- 数据存储一致性
		- 发生拷贝时直接在自身空间做修改
		- 改变任意变量不影响其他变量
			- 引用类型则不然，如string类型

### ArcheType
- made of chunks
	- 容器
		- 16KB
	- 不够再申请
- 内存连续性
- Cache命中
	- 每个实体的相同组件在内存中连续

---

## World

1. 组成
	- EntityManager
	- ComponentSystem
		- 主线程
		- JobComponentSystem
			- 同步点
				- 实体创建\销毁\组件添加删除
				- 主线程卡顿
		- IJobForEach<T1,T2>
	- Archtype
2. create
	- default
	- new world()
3. 多world间并行不互通
4. export scene to ecs
- Hybrid
	- scene批量转换ECS工具
	- 默认不支持Lightmap，需要自定义实现
	- SubScene
		- World.GetOrCreateSystem<SceneSystem>()
		- 流式加载
			- LoadSceneAsync()
			- UnLoadScene()
- GameObjectConversionUtilityConvertGameObjectHierachy()
	- GO->ECS
	- 只支持部分

---
							
## Debug

Entity Debugger
---

## 其他

1. 渲染
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