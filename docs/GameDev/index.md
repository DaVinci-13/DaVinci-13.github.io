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

---
### Unity Base
1. Unity Component
    - [UI](./u3d/u3d-ugui.md)  
        - [TextMeshPro](./u3d/u3d-textmeshpro.md)  
    - Camera  
    - [Transform](./render/render-transformation.md)  
    - Time  
    - Input
	    - InputManager
	    - InputSystem
2. [ScriptableObject](./u3d/u3d-ScriptableObject.md)

3. [UnityEditor](./u3d/u3d-editor-scripting.md)

4. Unity插件
    - LogViewer
    - EasyTouch
    - DOTween
	- Spine
    - [FGUI](./u3d/u3d-fgui.md)
    - Cinemachine
	- [Odin](./u3d/u3d-odin.md)

5. [DOTS](./u3d/u3d-dots.md)

6. 资源管理
    - [Resources](./u3d/u3d-resources.md)
    - [AssetBundle & Addresable](./u3d/u3d-addresable.md)

7. 物理
	- [碰撞](./physics/physics-collision.md)

8. 异步
    - [C#线程](./cs/cs-thread.md)
    - [C#异步](./cs/cs-async.md)
    - [Unity协程](./u3d/u3d-corotinue.md)
	
9. [热更新](./u3d/u3d-hotpatch.md)
	- 脚本热更新方案
	    - [xLua](./u3d/u3d-hotpatch-xlua.md)
	    - [ILruntime](./u3d/u3d-hotpatch-ilruntime.md)
	    - [hybridCLR](./u3d/u3d-hotpatch-hybridclr.md)

10. [原生交互:Android and IOS](./u3d/u3d-Android-and-IOS.md)

---
### Graphic 图形学
1. 渲染
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

2. 几何
	- [MVP变换](./render/render-mvp.md)
	- [向量计算](./render/render-transformation.md)
3. 光线追踪
	- [PBR](./render/render-pbr.md)
4. 动画模拟

---
### 动画
- [通用](./anime/anime-index.md)
- 动画类型
	- [序列帧动画](./anime/anime-sequence.md)
    - [刚体层次动画](./anime/anime-rigid.md)
    - [顶点动画](./anime/anime-vertex.md)
        - [表情动画](./anime/anime-morph.md)
    - [蒙皮动画](./anime/anime-skeletal.md)
    - [基于物理的动画](./anime/anime-physics.md)
    - [动画压缩](./anime/anime-pressed.md)
    - [高级动画技术](./anime/anime-tech.md)
- e.g.
	- [Mecanim](./u3d/u3d-anim-mecanim.md)
	- [Playerable动画](./u3d/u3d-anim-playable.md)

---
### 网络
- [协议](./network/net-proto-net.md):
    - TCP
    - UDP
    - Http
- [长/短 连接](./network/net-link.md)
- [状态同步与帧同步](./network/net-sync.md)
- [问题处理](./network/net-problem.md)
    - 流畅
    - 断线重连
    - 丢包重传
    - 粘包问题
    - 逻辑不同步
        - 随机数污染
		- 浮点精度
		- 逻辑顺序执行
		- 存储一致性
- [网络框架](./network/net-frame.md)
- [数据协议](./network/net-proto-data.md)

---
### [AI](./u3d/u3d-ai.md)
- 状态机
- 行为树
- AI
    - ML agent

---
### [FAQ](./FAQ.md)

---
## Unreal Engine 5 C++ Developer:Learn C++ & Make Viedeo Games | Udemy
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