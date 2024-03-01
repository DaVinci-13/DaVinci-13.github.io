---
title: Profiler-Unity3d Analysis 性能分析工具
layout: doc
---

# Unity3d性能分析

## Theory 理论
1. 开销： 函数开销=调用一次开销*调用次数
    - 调用一次开销=调用其他函数开销+自身开销

2. 优化热点：total高
3. 优化点
	- 调用时间
	- 调用次数

## profiler
1. 代码追踪API
```cs
Profiler.BeginSample()
Profiler.EndSample()
```
2. 面板参数
    - Self：自身开销
    - call：调用次数
    - total：总开销

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

3. 代码追踪新API
```csharp
private List<Transform> cubeList;
static readonly ProfilerMaker<int> profilerMaker = new ProfilerMaker<int>(name,param1Name);
void Update()
{
    using(ProfilerMaker.Auto(cubeList.Count))
    {
        //***
    }
}
```
