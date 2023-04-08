---
title: 变体
layout: doc
date:   2023-04-08 14:34:00 +0800
categories: render, unity3d, feature, compile
---

# ShaderLab变体
## multi_complie
e.g.
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
    - multi_compile D E
    - 6=3*2

---
## shader_feature
	- feature在打包（build）的时候不会把未使用的 variants 打进去， 因此应该使用shader_feature来声明那些material设置的关键词，全局代码使用的关键词最好用shader_compile来声明

---
## C#调用
	- Shader.EnableKeyword：启用全局关键字
	- Shader.DisableKeyword：禁用全局关键字
	- CommandBuffer.EnableShaderKeyword：使用CommandBuffer来启用全局关键字
	- CommandBuffer.DisableShaderKeyword：使用CommandBuffer可以禁用全局关键字
	- Material.EnableKeyword：为常规着色器启用本地关键字
		- 若不存在，则创建全局关键字
	- Material.DisableKeyword：禁用常规着色器的本地关键字
	- ComputeShader.EnableKeyword：为计算着色器启用本地关键字
	- ComputeShader.DisableKeyword：禁用计算着色器的本地关键字

---
## unity内置变体
- 类型
	- multi_compile_fwdbase 编译PassType.ForwardBase所需的所有变体。这些变体处理不同的光照贴图类型，并且启用或禁用了主方向光的阴影。
	- multi_compile_fwdadd 编译PassType.ForwardAdd的变体。这将编译变体以处理定向，聚光或点光源类型，以及带有cookie纹理的变体。
	- multi_compile_fwdadd_fullshadows 与相同multi_compile_fwdadd，但还包括灯光具有实时阴影的功能。
	- multi_compile_fog 扩展为多种变体以处理不同的雾类型（关闭/线性/ exp / exp2）。
- 跳过
	-  #pragma skip_variants

---
## 其他
### Graphics tiers and shader variants（图形层和着色器变体
 Unity将检查GPU的功能，并确定其对应的图形层，我们可以每一个图层创建一组着色器变体，并通过“#pragma ardware_tier_variants renderer（其中renderer是有的渲染平台）” 设置不同的图形层 （此功能仅与内置渲染管线容）
- platform
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
---

### Unity还会为每个着色器生成三个着色器变体
- UNITY_HARDWARE_TIER1  
	- //第一图形层（低）-对应于着色器定义UNITY_HARDWARE_TIER1。
	- //选择此级别的对象是：-不支持OpenGL ES 3的Android设备-iPhone 5、5C和更早的版本-iPod Touch第5代或更早版本-iPad 4或更早版本-iPad Mini第1代-台式机上的DirectX 9类硬件-HoloLens
- UNITY_HARDWARE_TIER2
	- //第二个图形层（中）-对应于着色器定义UNITY_HARDWARE_TIER2。
	- //选择此等级的用户包括：-支持OpenGL ES 3.0+的Android设备-iPhone 5S及更高版本-iPod Touch第6代-iPad Air及更高版本-iPad Mini第2代及更高版本-Apple TV
- UNITY_HARDWARE_TIER3
	- //第三图形层（高）-对应于着色器定义UNITY_HARDWARE_TIER3。
	- //选择此层可用于：-台式机上的OpenGL或DirectX 11+类硬件-Mac上的Metal