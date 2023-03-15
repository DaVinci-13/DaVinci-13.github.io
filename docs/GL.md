# GL

## Dev

### WebGL-ThreeJS

### Unity-ShaderLab

### UE5-BP

## API

### D3D

### OpenGL

### Vulkun

## DCC

### ps

### ae

- 前言

	- AK大神
	- 分形杂色

- 快捷键

	- Alt+Click 

		- 表达式

	- Alt+Home

		- 对齐到合成入点
		- 选中图层

	- Shift+A

		- 目标点

	- Ctrl+Alt+S

		- 添加到渲染队列

	- Ctrl+Shift+C

		- 预合成

	- F3

		- 效果控件面板

	- F4

		- 时间轴效果开关

	- F9

		- 关键帧

			- 平滑/缓动

				- 选中两个关键帧

	- M

		- 蒙版

	- P

		- 位置

	- T

		- 不透明度

	- U

		- 图层

			- 关键帧显示

	- PgUp

		- 向前一帧

	- PgDn

		- 向后一帧

- 小技巧

	- 渲染卡死恢复

		- 选中名称按Ctrl+D

	- 导入文件夹

		- 按Alt键拖入项目面板

- 功能

	- 编辑

		- 模板

			- 输出模块

	- 合成

		- 新建合成

			- Preset/预设
			- Resolution/分辨率
			- Start Timecode/开始时间码
			- Duration/持续时间

		- 添加到渲染队列/Add to Render Queue
		- 帧另存为 save frame as

	- Layer/图层

		- 新建

			- Ajustment Layer/调整图层
			- 摄像机

				- 摄像机选项

					- 缩放
					- 景深
					- 焦距
					- 光圈

		- 时间

			- Time Stretch/时间伸缩

		- Precompose/预合成

	- Effect/效果

		- Keying

			- Keylight

				- Screen Pre Blur

					- 在背景被抠除之前对遮罩进行模糊
					- 效果

						- View

							- Scree Matte

				- Screen Matte

					- Clip Black 修剪黑色

						- 提高黑色容差度

		- RG Trapcode

			- Particular

				- Emitter

					- Particles/Sec
					- Emitter Type
					- Velocity
					- Emitter Scale

				- Particle

					- Life 持续时间
					- Particle Type
					- Texture

						- Time Sampling

				- Rendering

		- 过时

			- color key/颜色键

		- 颜色校正

			- Curves/曲线

				- rgba

			- hue/saturation / 色相和饱和度

				- colorize/彩色化

			- brightness&contrast 亮度和对比度
			- coloroma 色光

				- Input Phase 输入相位
				- Output Cycle 输出循环

			- levels 色阶

				- Histogram 直方图

			- exposure 曝光

		- 风格化/Stylize

			- 动态拼接/motion tile

				- 主区域有偏移效果时小心使用
				- 

					- 镜像边缘
					- 输出宽度
					- 输出高度

			- 临界值RGB CC Threshold RGB
			- strobe 闪光灯
			- Glow 发光

		- 模糊和锐化/blur&sharpen

			- 高斯模糊 Fast Blur
			- 摄像机镜头模糊 Lens Blur

				- 模糊焦距 Blur Focal Distance

			- 定向模糊 Directional Blur
			- 复合模糊 Compound Blur

				- blur Layer

		- 模拟

			- CC Particle World

		- 过渡

			- Linear Wipe/线性擦除

				- 角度 Wipe Angle
				- 过度完成 Transition Complection
				- 羽化 Feather

		- 扭曲 Distort

			- Turbulent Displace 湍流置换

				- 大小 Size
				- 演化 Evolution

			- CC Page Turn 翻页

				- Fold Position

		- 声道 Channel

			- CC Composite

				- 在自己图层上再叠加一层原始素材

		- 生成 Generate

			- Ramp 梯度渐变
			- grid 网格

				- size from
				- width
				- border

		- 时间 Time

			- Posterize Time 色调分离时间

		- 透视 Perspective

			- 投影 Drop Shadow

		- 噪波与颗粒 noise&grain

			- 移除颗粒 remove grain

		- 遮罩 Matte

			- 简单阻塞工具 Simple Choker

	- Animation/动画 

		- Track  motion/跟踪运动
		- Keyframe Assistant 关键帧辅助

			- 序列图层

	- View 视图

		- 新建查看器

			- New Viewer

	- Window

		- Wiggler/摇晃器

			- Apply to
			- Noise Type/杂色类型

				- Jagged/锯齿

			- Dimension/维数
			- Frequency/频率
			- Magnitude/数量级

- 窗口 

	- 中

		- Monitor/监视器

	- 上

		- Mask/遮罩

			- 矩形
			- 圆角矩形
			- 椭圆
			- 多边形
			- 星型

		- Text/文字

			- 缩放：Shift+drag

	- 下

		- Timeline

			- Layer

				- Transform/变换

					- 

						- Rotation
						- Position
						- Anchor
						- Opacity

					- 关键帧

						- 
						- 

							- 关键帧辅助

								- Easy Ease 缓动
								- Easy Ease In 缓入
								- Easy Ease Out 缓出

				- Mask/蒙版

					- 方式

						- 无
						- 相减

					- 

						- Mask Feather/蒙版羽化
						- Mask Expansion/模板扩展

				- Text 文本

					- 动画制作工具

				- 材质

			- switch/开关

				- 运动模糊

			- Mode/模式

				- Multi/相乘
				- color 颜色

					- 只考虑下层的名都，而利用上层的色调和饱和度进行叠加
					- 保留原始图层的灰度细节

			- TrkMat 动态遮罩 

				- 亮度反转遮罩

			- 

				- 关键帧动画

	- 左

		- 项目

			- 解释素材

				- Main/主要

					- Sparate Field/分离场

						- 关 /Off

							- 无场模式

			- 创建代理

				- 影片

					- 渲染队列

			- 设置代理

				- 文件

	- 右

		- 预览
		- Tracker Controls/跟踪器

			- Track  motion/跟踪运动

- 实例

	- 1.简易天空替换 Basic Sky Replacement

		- Linear Wipe/线性擦除
		- color key/颜色键
		- Curves/曲线
		- Track  motion/跟踪运动

	- 2.消除隔行扫描 Deinterlace
	- 3.老电影画面 Old Film Look

		- Mode

			- Multi

		- 调整图层

			- 色相/饱和度

				- 彩色化

		- 高斯模糊

			- 重复边缘像素
			- 模糊度

		- Mask/蒙版

			- substract/相减
			- 蒙版扩展
			- 蒙版羽化

	- 4.AE101

		- 关键帧动画

			- 淡入淡出
			- 移动

		- 加减速
		- 预合成

	- 5.摄相机抖动 Camerashake

		- 添加关键帧
		- 摇晃器

			- Noise Type/杂色类型

				- Jagged/锯齿

			- Dimension/维数
			- Frequency/频率
			- Magnitude/数量级

		- 动态拼接

			- 镜像边缘
			- 输出宽高

				- 根据摇晃器数量级

		- 关键帧

			- 缓动

	- 6.三维合成 Compositing

		- 图片调成3D
		- 图片3D关键帧动画
		- 摄像机焦点
		- 调整图层

	- 7.去除瑕疵/祛斑 Blemish Removal

		- 创建蒙版

			- Ctrl+D复制图层
			- 第一层为matte

		- 临界值RGB CC Threshold RGB

			- 绿蓝拉到最大
			- 不是脸部尽量黑色

		- 颜色校正

			- 色相/饱和度

				- 饱和度最低

			- 色阶

				- 直方图

					- 亮度调到纯白

		- 新建调整层

			- 只影响白色部分

				- 移到第二顺位
				- TrkMat

					- 亮度遮罩  Luna Mate

			- 移除颗粒

				- 查看模式 Viewing Mide

					- 最终输出 Final Output

				- 杂色减少设置 Noise Reduction Setting

					- Noide Reduction 杂色减少

						- 1.5

			- 临时过滤

				- 运动敏感度

					- 0.925

		- matte

			- 高斯模糊

				- 模糊度

					- 6

		- 调整层

			- 增加颗粒

				- 查看模式

					- 最终输出

				- 预设

					- Kodak Vision 250D

				- 微调 Tweaking

					- 强度 Intersity

						- 0.2

					- 纵横比

						- 0.9

					- 柔化

						- 1.1

					- 大小

						- 1.2

				- 颜色

					- 饱和度

						- 0.25

	- 8.文字模糊飞入动画 TextBlurTitles

		- 新建文字

			- 文本

				- 动画按钮

					- 缩放

				- 动画制作工具

					- 添加

						- 模糊
						- 不透明度

		- 制作暗角

			- 新建蓝色纯色层
			- 新建黑色纯色层

				- 双击椭圆工具
				- 黑色层

					- 蒙版

						- 羽化

				- 蒙版模式 mask

					- 相减

		- 镜头光晕

			- 新建黑色纯色层
			- 效果

				- 生成

					- 镜头光晕

						- 镜头类型

							- 105mm

						- 图层模式

							- 相加

						- 效果

							- 光晕中心

								- 制作动画

		- 文字层

			- 模式

				- 相加

	- 9.使用代理 Proxies

		- 含义

			- 一段高清影像的低分辨率版本

		- 操作

			- 创建代理

				- 项目窗口右击序列
				- Create Proxy 创建代理

					- Movie

			- 弹出渲染队列对话框

				- Render Setting 渲染设置

					- Draft 草图

				- Output Moudle 输出模块

					- Lonssless with Alpha 带Alpha的无损

			- 点出输出模块设置

				- 格式

					- QuickTime Movie

				- 点击格式选项

		- 多个文件

			- 一一操作
			- 制作模板

	- 10.基础抠像技术 BasicColorKeying

		- Keylight
		- 简单阻塞工具
		- 色阶

	- 11.HDR&32bpc

		- 色深

			- 32位色深比8位色深有更丰富的颜色

		- 切换色深

			- 项目面板

				- 8bpc->32bpc

		- 调节32位色深下过于曝光的白色

			- 效果

				- 曲线 Curve
				- 色阶

					- 裁剪黑色、白色

		- View视图

			- 曝光

		- Effect

			- 色彩校正

				- 曝光度

	- 12.SliderShow 简洁幻灯片

		- 复制图层参数到其他图层

			- 选中参数
			- 复制粘贴

		- CC Composite
		- 图层自动排序

			- 动画

				- 关键帧辅助

					- 序列图层

		- 添加到渲染队列

	- 13.Assisted Suicide爆头效果

		- 运动跟踪

			- 跟踪运动

				- 选择位置、旋转
				- 选择没被遮挡的两个跟踪点
				- 跟踪

			- 新建一个空物体 Null Object

				- 储存跟踪数据
				- 操作

					- 图层

						- 新建

							- 空物体

					- 运动跟踪

						- 编辑目标

			- 应用

				- X和Y

		- 去掉脸

			- 设置alpha层

				- 复制视频图层
				- 设置

					- Time 时间

						- Freeze Frame 冻结帧

					- 不透明度

						- 50

					- 修建图层

						- alt+[

							- 刚开始爆头位置

						- alt+]

							- 冻结帧位置

					- 设置父级和链接

						- 空对象

			- 设置遮罩层

				- 新建白色固态层
				- 修剪图层

					- 按上一个图层

				- 不透明度

					- 50

				- 钢笔工具在头周围画遮罩

					- 蒙版

						- 羽化

				- 保证遮罩始终覆盖头

					- 逐帧改变头的旋转和位置
					- K帧

				- 放置新图层上方

			- 设置空对象不可见
			- 设置遮罩层不可见
			- 新图层

				- Trk.Matte

					- Alpha Matte

		- 导入爆头流血素材

			- 设置开始位置

				- 与爆头对齐

			- 调色

				- 色相/饱和度
				- 色阶

		- 导入枪口火花素材

			- 线性擦除
			- 羽化
			- 混合模式

				- Add

			- 曲线
			- 跟空对象建立父子关系

	- 14.简单漂色效果 Bleach Bypass

		- 色阶 levels

			- 增强对比度

				- input black
				- input white

		- 亮度和对比度
		- 高对比低饱和

			- 方法1

				- 复制图层

					- 删除效果
					- 关闭隐显
					- 混合模式

						- 颜色

			- 方法2

				- CC composite

					- original

						- color

				- 删除level

	- 15.2D DOF 二维景深

		- 摄像机镜头模糊

			- 设置深度贴图 depth map

				- 新建固态层
				- 渐变
				- 预合成

		- 方法

			- 1

				- depth图层

					- Ramp shape

						- Radial Ramp 径向渐变

					- Curves

						- 加深黑色
						- 增加高亮

			- 2

				- 模糊焦距

	- 16.Flipbook 翻书效果

		- 第一合成

			- 素材预合成

				- 保留所有属性

			- 素材合成

				- CC Page Turn

					- 折叠点

						- 关键帧动画
						- 表达式

							- 循环

					- Rederer

						- front

				- 定向模糊

					- 模糊长度

						- 关键帧动画
						- 表达式

							- 循环

				- 投影

			- 复制素材层

				- CC Page Turn

					- Renderer

						- back

				- 投影

					- 方向
					- 柔和度
					- 距离
					- 不透明度

		- 以第一合成创建第二合成

			- 复制素材层到次合成
			- 新素材层

				- 色调分离时间

		- 以第二合成创建第三合成

			- 图层

				- 时间

					- 启用时间重映射

						- K帧

					- 关键帧辅助

						- 缓入

					- 改变曲线

		- 闪光灯

			- 新建纯色层

				- 灰色

			- 闪光灯

				- 闪光

					- 使图层透明

			- 不透明度

				- 关键帧动画

			- 混合模式

				- Add

	- 17.3D_reflection 三维倒影

		- 场景

			- 文字层

				- 新建文字层
				- 预合成
				- 设为3D

			- 地板层

				- 新建固态层

					- 占满整个区域

				- 设为3D

			- 文字层放在固态层上
			- 地板层

				- 旋转至摄相机视线

			- 背景层

				- 新建纯色层

					- 适应合成大小

				- 至于最下方
				- 渐变 Ramp

			- 摄相机

				- 新建

			- 照明

				- 新建点光源
				- 新建环境光

			- 复制地板

				- 网格 grid
				- 图层混合模式

					- 叠加

				- 透明度

					- 50%

		- 渲染

			- 进入文字合成

				- 复制文字层

					- 纵向缩放

						- -100%

					- 衰减效果

						- 线性擦除

					- 透明度

						- 50%

				- 模糊衰减

					- 新建纯色层

						- 梯度渐变

							- 透明度

								- 50%

			- 新建调整层

				- 将3D形状分隔开

					- 改变渲染顺序

				- 放到text和grid之间

			- 反射2

				- 复合模糊
				- 文本

					- alt点击源文本

						- 连接到反射1源文本

	- 18.Light Stream Nano 广告光条纹

		- 新建

			- 新建固态层

				- 黑色
				- 命名BG

			- 复制固态层

				- 命名Particles

			- 新建调整层

				- 命名ColorFx

			- 新建灯光

				- 点光源
				- 命名 Emitter/发射器

			- 新建摄像机

				- 35mm

		- 新建粒子类型

			- 新建合成

				- Particle_50(50*50像素)

					- 持续时间

						- 1 frame

			- 新建白色固态层

				- 钢笔工具

					- 椭圆长条

				- 椭圆工具

					- 圆

		- 特效

			- 粒子层

				- trapcode particular

					- Emitter

						- 粒子数
						- 发射器类型

							- Emitter

						- 速度

							- 0

						- 缩放

							- 0

					- Particle

						- Life

							- 0

						- 粒子类型

							- 精灵

						- 时间采样

							- 自出生-循环

					- Rendering

						- Motion Preview

		- 灯光层

			- 位置表达式

				- wiggle(0.5,100)

					- 每0.5秒偏移一次
					- 每次偏移100pixel

		- 调整层

			- 色相/饱和度

				- 彩色化

			- 发光

		- 摄像机

			- 关键帧动画

				- 漂浮关键帧

	- 19.FPS Converter 帧率转化

		- 操作

			- 右击
			- 定义素材 Interpret Footage

				- Main

			- 修改合成大小

		- 运动伪像处理

			- 转换插件

	- 20.Saber 光剑

		- 1

			- 导入素材
			- 在制作光剑遮罩

				- 新建白色固态层

					- 调整透明度

				- 钢笔工具

					- 扣出光剑模型

				- 打开遮罩形状

					- 逐帧K帧
					- 逐帧调整遮罩位置

				- glow

		- 2

			- Andrew Kramer‘s VideoCopilot Saber插件

	- 21.Simulate Lighting 模拟枪口火光

		- action movie essential工具

	- 22.Fun with Ink 墨水飞溅效果

		- 素材制作

			- 新建合成

				- 新建白色纯色层

			- 效果

				- CC Particle World

					- 关闭Grid
					- 打开

						- Particle

							- Particle Type

								- Lens Convex 凸透镜

							- Max Opacity

								- 100%

							- Birth Size

								- 0.5

							- Death Size

								- 0

							- Size Variation

								- 85%

						- Producer
						- Physics

							- Gravity

								- 0

							- Velocity

								- 0.66

			- 截取静帧

				- 合成

					- 单帧另存为

						- psd

		- 制作动画

			- 导入psd

				- 创建合成

			- 制作暗角

				- 锁定

			- 添加文字
			- 帧动画

		- 墨汁溅落

			- 新建合成

				- 制作地面

					- 新建灰色固态层

						- 3D开关
						- 旋转90度
						- 向下移动

				- 墨滴

					- 新建黑色固态层

						- 钢笔工具

							- 抠图

					- 掉落

						- 关键帧动画
						- 运动模糊

					- 溅开

						- 导入psd
						- 色相/饱和度

							- 调为黑色

						- 旋转90度，移到地面
						- 遮罩

							- 遮罩扩展

								- 帧动画

	- 23.3D Lines 3d光束
	- 63.烟幕

		- 1

			- 正式

				- 新建合成

					- 预设

						- D1宽屏幕像素 

					- 持续时间

						- 10s

				- 拖入烟雾
				- 新建黑色背景(纯色)层
				- 烟雾

					- 旋转

						- 表达式

							- value+time*5

					- 3D

						- timeline

							- 3D图层

				- 新建摄像机

					- 预设

						- 35mm

			- 制作烟雾

				- 导入烟雾素材
				- 做遮罩matte让空白区域变透明

					- 新建固态（纯色）层 

						- 根据素材设置大小
						- 白色

					- 动态遮罩

						- 亮度反转遮罩

				- 调整图层校色

					- 新建调整图层
					- 校色

						- 色光

							- 输入相位

								- 获取相位：自

									- Alpha

							- 输出循环

								- 使用预设调板

									- Ramp Gray 灰阶图

								- 背景色

									- 蓝

								- Alpha通道

									- 0

				- 烟雾层随机运动

					- 湍流置换 

						- 大小：10
						- 演化

							- 表达式

								- time*100

			- 摄像机

				- 摄像机移动

					- 新建空物体
					- 设空物体为摄像机父物体
					- 空物体关键帧动画

			- 调整层

				- 校色

					- 曲线

		- 2

	- 95.场景重着色
	- 100.玻璃球
	- 104.粉碎的文字

		- 文字

			- 文字组件

				- 新建文字
				- 贴图

					- 拖入素材
					- TrkMat

						- Alpha通道模板

					- 颜色校正

						- 曲线

			- 复制文字

				- 斜面Alpha

					- Lighting Angle  灯光角度

						- 0

					- Light Intensity 灯光亮度

				- 模式 Mode

					- 叠加 Add

			- 复制文字

				- 斜面Alpha

					- Lighting Angle  灯光角度
					- Light Intensity 灯光亮度
					- Edge Thickness 边缘厚度

				- 模式 Mode

					- 叠加 Add

			- 文字相关

				- 预合成

		- 特效

			- CC Pixel Polly

				- Grid Spacing

					- 碎片大小

	- 115.球中的宇宙 

### pr

### sp

### sd

### blender

- 01.Introduce

	- small blue car

- 02

	- 3D Space
	- User Interface

		- Layout

			- 3d viewport

				- tool bar

					- hotkey：T

				- side bar

					- hotkey：N

				- split

					- RMB border
					- LMB drag corner

				- new window

					- Shift+LMB drag corner

				- swap

					- Ctrl+LMB drag corner

			- Outliner
			-  Property Editor
			- Timeline
			- Status bar

		- Editor Type

			- Genenral

				- base

					- 3D Viewport
					- Image Editor
					- UV Editor

				- Combine with real photoage and 3d shading

					- Compositor

						- 合成器
						- postprocess

					- Move Clip Editor
					- Video Sequancer

				- Other

					- Texuture Node Editor
					- Geometry Node Editor
					- Shader Editor

			- Animation
			- Scripting
			- Data

		- Workspace

			- type

				- Layout
				- Modeling
				- Sculpting

					- 雕刻

				- UV Editing
				- Shading
				- Animation
				- Compositing

			- Startup

				- create

					- File->New->General

				- adjustify

					- File->Default->Startup

				- reset

					- File->Default->Factory

		- tricks

			- Editor Fullscreen

				- Ctrl+Space

			- Shifting headers

				- MMB Scroll

			- Scroll through menus

				- Ctrl+MMB Scroll

			- Move Panel

				- LMB right-up corner "..."

			- Collapse/open multiple panels

				- LMB click a open panel, and move to others, still hold LMB

			- Cope/paste values

				- suspend value, and Ctrl C+V
				- not only values, but also colors

			- Eyedropper

				- 吸管

			- Quick Rename Object

				- F2
				- 3D Viewport

			- Qucik Favorites

				- Q

			-  Search

				- F3

		- short cut

			- take care you mouse cursor where

	- Navigating

		- Navigate in view

			- rotate

				- MMB

			- pan

				- Shitf+MMB

			- zoom

				- Crtl+MMB

		- Switch projection

			-  between Perspective and Orthographic

		- Camera
		- Walk navigation

			- Where

				- View->Viewport->Walk Navihation

			- qweasd
			- move fast

				- Shift

			- hotkey

				- diffrenet according by keyboard

		- other

			- Frame Selected

				- .(notepad comma)
				- View->Frame Selected
				- 重置视角到当前选择物体

			- Preferences

				- Orbit around selection
				- Zoom to Mouse Position
				- Auto Depth

					- do not work together with Orbit around selection

	- Save and Load

		- preferences
		- Quick Save

			- Save
			- Save As

### maya

### 3d max

## Theory

### source

- GAMES

	- GAMES101 / CS180

		- Linqi Yan
		- Overview of Computer Graphic

			- Topics

				- Resterization 光栅化

					- 实时

						- 30fps

					- 3维空间投影到2维屏幕

				- Curves and Meshs

					- 曲线
					- 曲面
					- 复杂曲面

				- Ray Tracing 光追

					- trade off
					- 实时光追

				- Animation / Simulation

			- 与CV的区别

				- CV

					- 猜测
					- 分析
					- 理解
					- Image Processing

				- CG

					- Rodeling
					- Simulating
					- Rendering

			- 推荐阅读

				- TigerBook

			- Dependencies

				- Basic mathematics

					- Linear Algebra 线性代数
					- calculus 微积分
					- statistics 统计

				- Basic physics

					- Optics 光学
					- Mechanics 力学

				- Misc

					- Signal processing 信号处理
					- Numerical analysis 数值分析

				- a bit of aesthetics 美学

		- Linear Algebra 线性代数

			- Vectors

				- dot products

					- 判定前后
					- 点乘结果为0

						- 互相垂直

				- cross products

					- a×b=A*b

						- a向量叉乘b向量=A矩阵乘b向量

					- 判定左右

			- Matrices

				- matrix-matrix
				- matrix-vector
				- multi

			- Cartesian Coordinates 笛卡尔/直角坐标

		- Transform 变换

			- why study

				- modeling
				- Viewing

			- 2D

				- Linear Transforms 二维矩阵形式

					- Scale

						- Reflection 镜像
						- reflection 翻转
						- Shear 切变/错切

							- 
							- y‘=y
							- x’=x+ay

					- Rotate

				- 三维矩阵形式

					- Homogeneous Coordinates

						- 问题

							- 
							- 
							- 

						- vector

							- (x,y,0)

						- point

							- (x,y,1)
							- (x,y,w) is (x/w, y/w, 1), w≠0

						- operation

							- v+v=v
							- v+p=p
							- p-p=v
							- p+p 中点

					- Translation 平移

						- Add a third coordinate

							- point-> (x,y,1)
							- vector-> (x,y,0)

								- vector=point-point

					- Affine map 仿射
					- 三大矩阵

						- 旋转
						- 平移
						- 缩放

				- Inverse 逆变换
				- 变换顺序

					- 绕原点旋转

						- 先平移到原点旋转后再平移回去

				- 变换的合成与分解

			- 3D

				- defination

					- homogenous coordinates

						- point

							- (x,y,z,1)

								- (x,y,z,w) is (x/w,y/w,z/w,1)

						- vector

							- (x,y,z,0)

					- use 4*4 matrix for affine transformation

				- transformation

					- 三大矩阵

						- Scale
						- Translate
						- Rotate

							- Euler angles
							- Rodrigues' Rotation Formula

								- Rotation by angle a around axis n
								- 

							- 四元数

					- MVP / view/Camera transformation

						- model transformation 模型坐标变换
						- view transformation 摄像机坐标变换

							- define

								- Position
								- lookat/gaze direction
								- up direction

							- The origin

								- up at Y
								- look at -z
								- (0,0,0)

							- Transfrom

								- 

									- View / Camera Transformation

								- find

									- why

										- difficult：view变换到origin，反之简单

								- inverse

									- 是正交矩阵

							- also known as ModelView Transform

						- Projection transfromation 投影

							- Orthographic projection 正交

								- canonical（正则，标准，规范） cube
								- Transform

							- Perspective projection 透视

								- how to

									- frustum to Cuboid

										- 

									- Orthographic

								- frustum  视椎体

									- aspect ratio 长宽比
									- (vertical) field of view 垂直可视角度 fovY
									- (0,t,n)

		- Rasterization 光栅化

			- Triangles

				- define

					- raster

						- raster==screen in German
						- Rasterize==drawing onto the screen

					- pixel

						- picture element

					- Canonical Cube to Screen

						- Viewport transform

							- matrix

					- 判断三角形与像素中心点的位置关系

						- triangles

				- Sample 采样

					- Evaluating  a function at a point is sampling
					- inside()？

						- sample if Each Pixel Center is Inside Triangle
						- 点在三角形内

							- Three Cross Products 三个叉乘

					- 边界

						- 不做处理
						- 特殊处理

							- opengl：上边、左边

				- Faster 加速

					- Bounding Box

						- 包围住图形的最小矩形

					- Incremental Triangle Traversal

						- suitable for thin and rotated triangles
						- 从三角形最左下方的点依次向上向右枚举可能点

				- display

					- bayer pattern

						- more green

			- Aliasing(Jaggies) 走样（锯齿）

				- define

					- Artifacts 瑕疵

						- exp

							- Jaggie 锯齿
							- Moire pattern 摩尔纹

								- 原因：隔行采样

							- wagon wheel illusion (False Motion)

						- due to sampling : Signals are changing too fast(high frequency),but sampled too slowly

					- signal
					- blur aliasing

						- sample then fliter

				- anti

					- filter then sample 模糊处理

						- define

							- Flitering 滤波

								- 去掉一系列频率
								- high-pass fliter

							- Frequency Domain

								- define

									- Fourier Transform

								- Higher Frequencies Need Faster Sampling

							- Filtering=Convolution 卷积(=Averaging)

								- Convolution

						- 原理

							- 通过滤波器去掉锯齿边界

					- how to reduce aliasing error

						- Increase sampling rate
						- Antialiasing Sampling

							- theory

								- Antialiasing by Computing Aberage Pixel Values

									- 根据三角形对像素正方形区域的覆盖率averaging视作贡献Convolving决定颜色的深度filtering，覆盖越多，颜色越深
									- 1-pixel box-blur

							- Application

								- MSAA：Antialiasing By Supersampling

									- Average the NxN samples "inside" each pixel
									- Supersampling 超采样 : Result
									- cost

										- Canculation

									- 在1-pixel box-blur再找到均匀四点进行采样

								- FXAA：Fast Approximate AA

									- CV图像匹配找到边界
									- 将有锯齿边界换为无锯齿

								- TAA：Temporal AA

									- 复用上一帧信息
									- MSAA+时间维度

				- Super resolution / super sampling

					- 

						- 研究问题：想要将低分辨率图拉伸为高分辨率图
						- 例如：PS将720*480的图片改为1280*720

					- DLSS：Deep Learning Super Sampling

						- 实质：猜测

			- Z-Buffer

				- define

					- visibility / occlusion
					- Painter's Algorithm

						- Inspired by how painters paint
						- Paint from back to front 先渲染远处物体
						- overwrite in the framebuffer
						- Requires sorting in depth(O(n log n) for n triangles)
						- problem

					- Z-Buffer

						- Store currnt min. z-value for each sample(pixel)

							- 存储每个像素的深度值
							- 
							- 

				- Algorithm

					- 
					- Complexity

						- O(n)

							- 

		- Shading 着色

			- shadows mapping 阴影

				- define

					- An Image-space Algorithm
					- problem

						- must deal with aliasing artifacts

					- key idea

						- the points Not in shadow must seen both

							- bt the light
							- by the camera

				- do

					- render from light

						- Depth image from light source 从光源看向场景记录深度

					- Render from Eye；
Project to light 

						- Standard image (with depth) from eye
						- Project visible points in eye view back to light source

							- 从点到光源若已经有更低的深度值，则该点为被遮挡点

					- point->pixel

				- problem

					- 

				- hard shadow vs. soft shadow

					- soft shadow 半影

			- shading

				- definition

					- applying a material to an object
					- 
					- 

				- Shading Model

					- Blinn-Phong Reflectance Model

						- define

							- lambert's cosine law

								- In general, light per unit area is proportional to cosθ=I·n

							- Light Falloff
							- Specular

								- 

						- Lambertian (Diffuse) Shading

							- 漫反射与观察方向无关

						- Specular Term

							- 

								- 半程向量即角平分线方向
								- 反射方向与观察方向接近程度 正相关于 法线方向与半程向量接近程度
								- Cosine Pwer Plots 高光系数

									- 一般来说：100-200
									- 直接用余弦高光可见范围太大

						- Ambient Term

							- 环境光在本模型被简化为常熟颜色

						- Blinn-Phong Reflectance

							- 

				- Shading Frequency 着色频率

					- define

						- flat shading: 逐三角形法线着色
						- Gourand shading: 逐顶点法线着色

							- 相邻面法线顶点求平均

						- Phong: 逐像素法线着色

					- shader

			- Graphics(Real-time Rendering) Pipeline

				- 渲染管线

			- Texture Mapping 纹理映射

				- Surfaces are 2D

					- 三维物体表面都是二维的

				- how to

					- 参数化
					- 美术

				- uv

					- Texture Coordinate 纹理坐标
					- (u，v)=(0,0)-(1,1)
					- tiled 无缝贴图

						- wang tiled

				- Interpolation Across Triangles: Barycentric Coordinates 重心坐标

					- why

						- smoothly varying values across triangles
						- Specify values at vertices

					- want
					- how

						- Barycentric Coordinates

							- 
							- 
							- 

						- Applying Texture

							- 
							- problem：Texture Magnification

								- 纹理太小

									- solve

										- Bilinear Interpolation 双线性插值
										- Bicubic

									- 纹理太小而要贴图的模型太大

								- 纹理太大

									- 
									- 
									- solve

										- superaliasing

											- 用多个采样点

										- Range Query

											- define

												- Point Query vs. (Avg.) Range Query
												- 范围查询求平均值

											- Mipmap

												- 特点

													- fast
													- approx
													- square 方形

												- Mip hirechy：提前计算一张纹理的所有开方直到1*1的均值贴图
												- 优点

													- 只增加存储量 1/3(=1/4+1/16+1/64+……)

												- 查询

													- D=log L
													- Trilinear Interpolation

														- 

												- 缺点

													- Overblur

											- Anisotropic Filterring 各向异性过滤

												- solve

													- 

												- define

													- 

												- x

													- 压缩几次

												- 代价

													- 存储开销渐进于原来的3倍

											- EWA filtering

												- 

				- Texture

					- Environment Lighting
					- Environment Map

						- Ulta teapot

					- Spherical Map-Problem
					- CubeMap
					- Bump Mapping 凹凸/法线贴图

						- textures can affect shading

					- Displacement mapping 位移贴图

						- 改变vertex
						- 代价

							- 模型必须足够精细

					- dynamic tessellation 动态曲面细分

						- DirectX
						- 根据实际情况对模型计算生成新的顶点

					- Perlin Noise 柏林噪声
					- Precomputed Shading

						- Ambient occlusion 环境光遮蔽

					- Volume Rendering 体积渲染

						- 3D Textures

		- Geometry 几何

			- Introduce

				- Implicit 隐式

					- Based on classifying points: Points satisfy some specified relationship
					- 缺点：Sampling Can Be Hard
					- 优点：Inside/ outside Tests Easy
					- e.g.

						- Algebraic 数学公式
						- CSG：Constructive Solid Geometry
						- Distance Functions 距离函数

							- SDF

						- Level Set Methods
						- Fractals 分形

				- Explicit 显式

					- All point are given directly
					- via paramter mapping
					- Sampling is Easy
					- Inside/ outside Tests Hard
					- e.g.

						- Point cloud
						- Polygon Mesh

							- The Wavefront Object File (.obj) Format

								- 8个点
								- 6个法线
								- 12-24个纹理坐标
								- f 顶点索引/纹理uv坐标索引/法线索引

			- Curve 

				- Bezier Curves

					- de Casteljau Algorithm
					- Algebraic Formula

						- 
						- Bernstein Polynomials

					- Properties

						- Affine transformation property 仿射变换性质

							- Transform curve by transforming control points

						- Convex hull property 凸包性质

							- Curve is within convex hull of control points

					- Continuity

						- C0
						- C1

				- spline 样条

					- define

						- 连续曲线是有一些列的点控制的

					- B-splines
					- NUBRS

				- more

			- Surface

				- Bezier Surfaces

					- 4*4 array of control point

						- 4*1 horizontal Curves *4
						- Vertical Curves = 4* points

					- from Bezier Curves
					- uv

						- u：Horizontal time
						- v：vertical time

				- Mesh Operations：Geometry Processing

					- Mesh subdivision 细分

						- upsampling
						- do

							- create more triangle
							- tune their position

						- Loop Subdivision

							- Loop：family name
							- only for triangle

						- Catmull-Clark Subdivision

							- General Mesh
							- result

								- quad

					- Mesh simplification

						- downsampling
						- edge collapsing 边坍缩

							- Quadric Error Metrics 二次误差度量
							- 二次误差

					- Mesh regluarization

		- Ray Tracing 光追

			- why

				- Rasterization couldn't handle global effects well

					- soft shadows
					- glossy reflection
					- indirect illusion

						- 光线弹射多次

				- Rasterization is fast, but quality is relatively low

					- real-time

				- Ray tracing is accurate, but is very slow

					- offline
					- ~10K CPU core hour render one frame

			- define

				- light rays

					- light travels in straight lines (though this is wrong)
					- light rays  do not "collide" with each other if they cross (though this is wrong) 本课程认为光线间不会碰撞
					- light rays travel from the light sources to the eye (but the physics is invariant under path reversal - reciprocity)

						- （光线可逆性）CG认为观察体可以发出实现沿着光路到达光源

				- do

					- Ray casting 光线投射

						- Generating Eye Rays
						- Pinhole Camera Model

			- Whitted-Style (Recursive) Ray Tracing

				- invent by T.Whitted, 1979

			- Ray-Suface Intersection 交点

				- Ray Equation
				- Ray Intersection With Sphere
				- Ray Intersection With Implicit Surface
				- Ray Intersection With Triangle Mesh

					- why

						- Rendering
						- Geometry

							- inside/outside test

					- compute

						- Ray Intersection With Each Triangle
						- by plane

							- Ray Intersection With Triangle

								- Ray-plane intersection
								- triangle is in plane
								- test if hit point is inside triangle

							- Plane Equation

								- define by normal vector and a point on plane

						- Moller Trumbore Algorithm

							- 

								- compute by Cramer's Rule
								- 重心坐标表示的三角形平面上的点

									- 若点P在此三角形内，三个系数均大于0

			- Accelerating Ray-Surface Intersection

				- (Simple ray-scene intersection) Problem

					- Very slow
					- Naive algorithm=pixels*objects(*bounces 光线弹射)
					- exp

						- San Moguel Scene, 10.7M triangles
						- Plant Ecosystem, 20M triangles

				- Bounding Volumes 包围盒

					- define

						- 一个复杂object可以用一个简单object完全包围

							- 3D->box

						- box is the intersection of 3 pairs of slabs
						- Axis-Aligned Bounding Box(AABB) 轴对齐包围盒

					- 原理

						- 若光线连物体的包围盒都无法碰到，则绝对无法与物体有交点

					- 光线与AABB包围盒求交

						- Ray Intersection with Axis Aligned Box

							- 2D

								- 2D形状为2个对面所围成
								- 分别计算光从2组对面的进入时间与离开时间
								- 光在2D里的时间=最早离开时间-最迟进入时间

							- 3D

								- 思想同上

							- 问题处理

								- t_enter<t_exit

									- has intersection

								- t_exit<0

									- no intersection
									- t_enter

										- point in 2D/3D
										- has intersection

							- result: iff(iff, 当且仅当)

								- t_enter<t_exit && t_exit>=0

						- why AABB

							- 容易计算

				- Using AABBs to accelerate

					- Preprocess-Building Acceleration Grid

						- Find bounding box
						- Create grid
						- Store each object in overlapping cells

					- Ray-Scene Intersection

						- Grid

							- Step through grid in ray traversal order
							- For each grid cell

								- Test intersection with all objects stored at that cell
								- Rasterize a line

									- 根据光线方向选择要查询的cell

							- Speed Effect

								- Heuristic

									- cells=C*objs
									- C约等于27 in 3D

								- 效果最好

									- 规则图形
									- 分布均匀

						- Spatial Partition 空间划分

							- Oct-Tree 8叉树

								- 每一次box均匀分成8份

							- BSP-Tree

								- 每一次沿某个方向分成两份

							- KD-Tree

								- 每一次box沿某条轴分成均匀两份
								- 顺序：x y z
								- Data Structure

									- 

								- problem

									- 如何判断box与triangle(object)有交点
									- 一个object可能会出现在多个Box中

						- Object Partition 物体划分 & Bounding Volume Hierarchy（BVH）

							- how

								- 找到一堆物体的包围盒
								- 将物体分成两堆

									- how to subdivide a node

										- Choose a dimension
										- Heuristic

											- Alway choose the longest axis
											- Split node at location of median object 找到物体的中位数

												- 快速选择

													- 对一个大小为n数字序列搜索其中第i大的数
													- O(n)

								- 分别求每堆的Box

							- problem

								- 包围盒可能相交

							- BVH

								- Data Structure

			- Basic radiometry 辐射度量学

				- define

					- 描述光照

				- properties of light

					- Radiant energy
					- Radiant(luminous 流明) flux(power)

						- 辐射通量
						- 单位时间的辐射能量
						- Energy per unit time单位时间通过单位平面的光子数量

					- intensity

						- define

							- power per unit solid angle一个光源单位立体角在单位时间内的辐射能量
							- where

								- Light Emitted From A Source

						- 

							- solid Angles 立体角

								- 

									- Differential Solid Angles 微分立体角

								- ratio of subtended area on sphere to radius squared
								- 单位

									- sr(steradians)

								- exp

									- sphere

										- 球的立体角

						- e.g.

							- Modern LED Light

					- irradiance

						- define

							- power per unit projected area 一个单位表面接收到的辐射能量

								- 只考虑垂直分量

							- where

								- Light Falling On A Surface 

					- radiance

						- define

							- where

								- Light Traveling Along A Ray 光在传播中的辐射量

							- power per unit solid angle, per projected unit are
							- 某个方向的irradiance

				- Reflection at a Point

					- Bidirectional Reflectance Distribution Fuction (BRDF)

						- define

							- 光线入射一个单位表面，此单位表面将在各个方向反射多少能量（如何分配）

								- Differential irradiance incoming 单位表面接收到irradiance
								- Differential radiance exiting 转化为（每个个方向的）radiance

							- 某个方向的radiance/单位表面的irradiance

								- 单位表面的irradiance=入射光在某个立体角给单位表面的irradiance=某个立体角方向的radiance*立体角

							- 光线和（不同材质）物体如何作用

						- 子主题 3

					- The Reflection Equation

						- 所有方向的光线在一个观测点在相机方向的反射即为合成效果
						- Recursive

							- 考虑二次反射（光线弹射），则该方程为递归的

						- 光源类型

							- 点光源

								- 求和

							- 面光源

								- 积分

						- 多次反射将会收敛

							- 能量守恒
							- 级数收敛

						- 漫反射为半球方向

							- 

				- The Rendering Equation

					- 自发光radiance+反射方程radiance
					- 算子方式

						- 
						- Binomial Theorem

					- 论文

						- kajiya 86

			- 数学

				- Probability 概率论

					- Random Variables 随机变量
					- Probabilities 概率
					- Expected Value 期望
					- 古典概率
					- Probability Distribution Fuction (PDF): Continuous Case 概率密度函数：连续函数期望
					- Expected Value of a Fuction of a Random Variable

				- Monte Carlo Integration 蒙特卡洛积分

					- 黎曼积分
					- what & how

						- estimate the integral of a function by averaging random samples of the function‘s value

					- function

			- Path Tracing

				- The Problem of Whitted-Style Ray Tracing

					- color bleeding

						- The Cornell box

				- theory

					- Monte Carlo Integration On Render Equation

						- 
						- 

							- 半球方向
							- 均匀采样

						- means

							- A correct shading algorithm for direct illumination 一个正确的着色点反射能量算法

						- 全局光照

							- 直接光照

								- 如上

							- 间接光照

								- 求反射物的直接光照
								- 递归

					- problem

						- Explosion of rays as bounces go up 因光线弹射而计算量指数爆炸

							- 解决

								- 只采样一个随机方向的光线（而不在半球均匀采样），令N=1

									- N!=1, Distributed Ray Tracing 分布式光线追踪, 必会出现指数爆炸
									- N=1, Path Tracing 路径追踪

						- 递归如何停止

							- Russian Roulette (RR)

								- 最后结果除以概率可以得到无偏估计期望

									- E=P*(Lo/p)+(1-p)*0=Lo

										- p的概率有Lo的值
										- 1-p的概率为0

								- 每次有P的概率存活期望有多少次

									- 1-p

							- 以此方式决定停止追踪

					- 光线浪费

						- problem：采样点找到光源路径完全随机

							- 以渲染点在半球面均匀采样发射射线寻找光源
							- 射线数量不能确定

						- 解决

							- 寻找（对于渲染点均匀采样）更好的采样方法
							- 微积分思想，将渲染方程对采样点积分替换为对光源积分

								- 立体角
								- 面光源的面积
								- 光源法线对渲染点的角度
								- 光源坐标
								- 渲染点坐标

							- 面光源

								- 

				- Alert

					- Make sure that the indirect ray return 0 when it hits light sources (already calculated in direct illumination)

				- result

					- light source

						- 对光源采样
						- 遮挡

							- 碰撞检测

								- 若被遮挡，值为0

					- Contribution from other reflectors

						- 对非光源递归采样

				- Some Side Note

					- point light source

						- hard
						- a resolution

							- very small area light source

					- Path Tracing is PHOTO-RELASTIC
					- vs.

						- Previous

							- Whitted-style ray tracing

						- Modern

							- The general solution of light transport

								- Unidirectional & bidirectional path tracing
								- Photon mapping
								- Metropolis light transport
								- VCM/UPBP

					- Things we haven't covered/ won't cover 未提及的事情

						- Uniformly sampling the hemisphere 均匀采样的实现
						- best pdf

							- importance sampling 重要性采样理论

								- 求对某种形状函数的最好采样方法

						- random number

							- low discrepancy sequences

						- sample the hemisphere and the light 结合不同采样方法

							- multiple imp. sampling, mis

						- The radiance of a pixel is the average of radiance on all paths passing through it

							- pixel reconstruction filter

						- the radiance of a pixel is not the color

							- gamma correction 伽马矫正
							- curves
							- color space

		- Materials and Appearance 材质与外观

			- material=BSDF

				- Diffuse/Lambertian Material
				- glossy material
				- Ideal reflective / refractive material (BRDF*)
				- S：shatter 散射

					- BSDF=BRDF+BTDF

			- Perfect Specular Reflection 反射

				- Top-down view
				- normal

			- Specular Refraction 折射

				- caustics
				- Snell's Law

					- Snell's Window / Circle

						- total internal reflection

				- BTDF

					- T:transmit 折射

			- Fresnel Reflection / Term 菲涅尔项

				- Relectence depends on incident angle (and polorization of light)
				- e.g.

					- 

						- S polarization
						- P polarization
						- unpolarized

					- Conductor

				- Formulae

					- Schlick's approximation

						- 近似

			- Microfacet Material

				- Microfacet Theory

					- define

						- microsurface
						- macrosurface

					- Rough surface

						- Macroscale

							- flat
							- rough

						- Microscale

							- Specular
							- bumpy

					- individual elements of surface act like mirrors

						- Known as Microfacets
						- Each microfacet has its own normal

				- Microfacet BRDF

					- key: the distribution of microfacets' normals

						- Concentrated == glossy
						- Spread == diffuse

					- grazing angle
					- e.g.

						- PBR

			- Properties of BRDFs

				- Non-negativity 非副
				- Linearity
				- Reciprocity principle 可逆性

					- 交换入射出射，值相同

				- Energy conservation 能量守恒
				- Isotropic vs. Anisotropic 各向同性 vs .各向异性

					- 区分材质的方法
					- Key：directionality of underlying surface
					- BRDF/材质与绝对方位角是否有关与绝对方位角是否有关
					- e.g.

						- Nylon
						- Velvet

			- Measuring BRDF 测量

				- why
				- Image-based

					- e.g.

						- gonioreflectometer

					- 不同位置的相机测量在不同位置光源下的点
					- problem

						- curse of dimensionality 维度灾难
						- Improving effeciency

					- storge: Representing Measured BRDFs Desirable qulities 存储BRDF结果

						- MERL BRDF Database

							- 测量BRDF

								- 90*90*180

							- BRDF库

		- Advance Topics In Rendering

			- Biased vs. Unbiased Light Transport

				- define

					- Biased

						- consistent 收敛

					- Unbiased 无偏

				- BDPT (Bidirectional Path Tracing, 双向路径追踪)

					- 从光源和摄像机同时进行路径追踪
					- difficult and slow
					- e.g.

						- 漫反射场景

				- MLT (Metripolis Light Transport)

					- Markov Chain Monte Carlo, MCMC

						- 统计学工具
						- Jumpling from the current sample to the next with some PDF, 从当前样本得到相邻样本

					- key idea

						- locally perturb an existing path to get a new path

					- good at

						- locally exploring difficult light path

					- 蒙特卡洛方法采样效果

						- 当f(x)与pdf形状越接近，效果越好

							- 方差越小

					- e.g.

						- 漫反射场景
						- caustics
						- SDS (Specular Diffuse Specular Path)

					- Cons

						- estimate the convergence rate
						- does not guarantee equal convergence rate per pixel
						- usually produces "dirty" results
						- usually not used to render animation

				- Photon Mapping 光子映射

					- biased
					- two-stage

						- Stage 1: photon tracing
						- Stage 2:photon collection (final gathering)
						- Calculation - local density estimation

							- KD-tree
							- 计算光子密度N

					- good at

						- SDS
						- caustics

				- Vertex Connection and Merging, VCM

					- A combination of BDPT and Photon Mapping

				- Instant Radiosity, IR

					- sometimes also called many-light approches
					- Virtual Point Light, VPL
					- Pros

						- fast
						- diffuse scenes

					- cons

						- cannot glossy
						- Spikes will emerge when VPLs are close to shading points

			- Advanced Appearance Modeling

				- Non-surface models

					- Participateing Media 散射介质/参与介质

						- e.g.

							- cloud
							- Stomakhin et al. 2014

						- Phase Function, 相位函数
						- Rendering

					- Hair Appearance

						- Image courtesy of Chiwei Tseng
						- Kajiya-Kay Model

							- Yuksel et al.2008

						- Marschner Model

							- 3 types of light intersection

								- TT
								- TRT
								- R

							- Glass-like cylinder

								- cortex (absorbs)
								- cuticle

							- e.g.

								- Marschner et al.2003
								- d'Eon et al. 2011

						- cons

							- mass-computing

					- Fur Appearance

						- Human Hair vs. Animal Fur

							- biology

								- Medulla 水质
								- cuticle
								- cortex

						- Double Cylin Model -- Lobes

							- 3 types of light intersection

								- R
								- TT
								- TRT
								- TTs
								- TRTs

							- Linqi Yan

					- Granular Material 颗粒材质

				- Surface models

					- Translucent Material:Jade 透光材质

						- e.g.

							- Jade 玉石
							- Jellyfish 水母

						- Subsurface Scattering 次表面散射

							- BSSRDF：generalization of BRDF
							- exitant radiance at one point due to incident different irradia at another point

						- Dipole Approximation

							- Jensen et al. 2001
							- 双光源近似此表面散射效果

								- 分别在表面双方

					- Cloth 布料

						- physic

							- Fiber
							- Ply
							- Yarn

						- Render

							- weaving pattern

								- limitation

									- valvet

							- Participating Media
							- Actual Fibers

								- e.g.

									- shuang et al. 2012

					- Detailed/Glinty Appearance / MicroSurface

						- problem

							- too perfect but unrealstic

						- e.g.

							- Yan et al. 2014,2016
							- Metallic flakes 亮片

						- Recent Trnd

							- Wave Optics 波动光学

								- e.g.

									- Yan et al. 2018

				- Procedural appearence 程序化生成表面

					- Noise Fuction

						- 3D

					- e.g.

						- Houdini

		- Cameras, Lenses and Light FIelds, Color and Perception

			- Imaging=Sythesis+Capture
			- Camera

				- parts

					- Sensor 传感器

						- records irradiance

					- Shutter 快门

				- theory

					- Pinhole Image Formation 小孔成像
					- Lens 透镜

				- concept

					- FOV, Field of View

						- f, Focal Length 焦距
						- h, height of sensor

							- 35mm-format film, 35mm胶片

					- Exposure 曝光

						- Aperture size 光圈大小

							- f-stop

								- more big，Aperture more small
								- N=f/A

									- N: focal length
									- A: diameter of aperture, g光圈直径

						- Shutter speed

							- Motion blur 运动模糊

								- 快门时间越长，运动模糊越严重

							- rolling shutter
							- Fast and Slow Photography

						- ISO gain 感光度

							- more big,  noise more many

			- Lens 透镜

				- Thin Lens Approximation

					- theory

						- Real Lens are complex
						- ideal Thin Lens

							- Focal Point

								- can be arbitrarily changed

						- Gauss‘ Ray Tracing Construction

					- Defocus Blur

						- define

							- Circle of Confusion, CoC, is proportional to the size of the aperture. CoC与光圈大小成正比

				- Ray Tracing Ideal Thin Lenses

					- (One possible) Setup

						- Choose sensor size, lens focal length and aperture size
						- Choose depth of subject of interest z

					- Rendering

						- For rach pixel x1 on the sensor
						- Sample random x2 on lens plane
						- you know the ray passing through the lens will hit x3
						- estimate radiance on ray x2->x3

				- Depth of Field 景深

					- define

						- 聚焦平面附近成像清晰（形成的CoC较小）的一段距离

			- Light Fields / Lumigraph 光场

				- define

					- Ray

						- 4D

							- 2D location
							- 2D direction

						- to point confirm Infinite line

					- The surface of a cube holds all the radiance information due to the enclosed object

				- theory

					- The Plenoptic Function 全光函数

						- e.g.

							- Holographic movie 全息电影

					- 2 plane confirm a Lumigraph

						- Stanford camera array

							- 在uv平面每个点存储一个st平面的不同角度成像

						- Integral Imaging ("Fly's Eye" Lenslets)

				- Light Field Camera

					- The Lytro Light Field Camera

						- Computational Refocusing 后期聚焦

					- problem

						- Insufficient spatial resolution 分辨率不足
						- High cost
						- Computer garphic is trade-off

			- Physical Basis of Color

				- concept

					- The Visible  Spectrum of Light  可见光光谱
					- Spectral Power Distribution, SPD, 谱功率密度

						- Describe distribution of energy by wavelength 光在各个波长上的分布
						- properties

							- Linearity

					- Color

						- a phenomenon of human perception
						- Biological Basis of Color

					- Metamerism 同色异谱现象

				- Color Space / gamut 色域

					- Additive Color

						- sRGB

							- CIE RGB Color Matching Experiment
							- 色域小于CIE XYZ

						- CIE XYZ

							- CIE XYZ Color Matching Experiment

								- Y is luminance 亮度

						- HSV(Hue-Sataurtion Value) Color Space

							- Hue 色调

								- 颜色

							- Saturation 饱和度

								- (白, 色)

							- Lightness (or Value) 亮度

								- (黑, 色)

						- CIELAB Space (AKA L*a*b)

							- Opponent Color Theory  互补色

					- concept

						- Color Reproduction / Matching
						- Chromaticity 色度

							- CIE XYZ 固定Y
							- XYZ归一化得到x，y，z

					- define

						- 所有可能的颜色

					- Subtractive Color Space

						- CMYK

							- Cyan Magenta Yellow Key
							- Key 黑色

								- CMY可以合成黑色
								- 打印

									- 黑色成本较低

				- Not coverd

					- HDR，High-Dynamic Range 高动态范围图像

						- 摄影

							- 不同曝光度的图片通过对每个Object的智能选取合成一张图片

						- CG

							- 方法

								- HDR 通过 Tone Mapping (色调映射) 映射到LDR

									- 非线性

								- 泛光

							- define

								- LDR-8位色

									- color blending 色带问题

								- HDR-10+色深

									- 更大的对比度

										- 更多的亮度

									- 更宽的色域

					- gamma correction

						- 把PT得到的radiance矫正颜色
						- 原因

							- 原图是线性的，但显式设备颜色显示非线性，若直接显示则图像失真

								- 若不进行gamma矫正则偏暗

									- 大多数游戏

								- 非线性原因

									- 人眼对暗部的变化更加敏感，而对亮部变化其实不是很敏感
									- Youtube：Color is Broken

						- 原理

							- 在显示设备显示之前进行预补偿（一个与显示设备的非线性函数相反的函数），使得最后输出线行结果

						- 渲染

							- display gamma=2.2

								- 假设大部分游戏使用没有校正过的显示器，这些显示器的display gamma可以粗略地认为是2.2。（对于更高质量要求的游戏，可以让你的游戏提供一个伽马校正表格，来让用户选择合适的伽马值。）

							- 硬件gamma矫正
							- 手动矫正

		- Animation / Simulation

			- define

				- An extension of modeling
				- sequence of images provide a sense of motion

			- application

				- Film

					- 24fps

				- Video

					- 30fps

				- VR

					- 90fps

			- keyframe Animation

				- Interpolation 插值

					- linear
					- smooth / controllable

			- Physical Simulaition

				- theory

					- Newton's Law

				- define

					- generate motion of objects using numerical simulation

				- good at

					- 无穿模

				- Mass Spring System 质点弹簧系统

					- theory

						- define

							- vector
							- v, velocity
							- a, acceleration

						- idealized spring

							- Hooke's Low

								- Spring coefficient: stiffness
								- 
								- 

							- 0 length

						- Non-Zero Length Spring

							- l:rest length
							- problem: oscillates forever 永远运动

								- 动能势能不断转换
								- solve

									- 摩擦力

						- Damping force 摩擦力

							- problem: slows down all motion

								- 只有外部力，没有内部损耗
								- solve

							- 

								- Direction from a to b
								- Relative velocity projected to the direction from a to b (scalar)

									- Relative velcity of b, assuming a is static
									- 只在ab方向受力才会引起形变

						- Structures from Springs

							- problem

								- not resist shearing
								- not resist out-of-plane bending

							- solve

								- each quad point connection

									- 正方形四个点之间建立弹簧

								- skip connection

									- (水平竖直方向)隔点建立弹簧

					- Aside

						- FEM， Finite Element Method

				- Particle Systems

					- challenge

						- many particles
						- acceleration structures

							- e.g.

								- neraest particles for interactions

					- Animation

						- Define and Canculate forces on each particle

					- Forces

						- Attraction and repulsion forces
						- Damping force
						- Collison

					- e.g.

						- Simulated Flocking as ODE
						- Molecular Dynamics
						- Crowds + "Rock" Dynamics

				- Forward Kinematics, FK （正）运动学

					- theory

						- Articulated skeleton

							- Topology
							- Geometric relations from joints
							- Tree structure

						- Join types

							- Pin

								- 1D

							- Ball

								- 2D

							- Prismatic Joint

								- Translation

					- Pros and Cons

						- Strengths

							- Direct control
							- Implementation is straightforward

						- Weaknesses

							- Animatrion may be inconsistent with physics
							- Time consuming for artists

				- Inverse Kinematics, IK 逆运动学

					- problem

						- Multiple solutions in configuration type
						- Solution mat not always exist

					- solution

				- Rigging 骨骼绑定

					- 通过控制点控制model
					- 子主题 2

				- Blend Shapes

					- 动画融合
					- 子主题 2

				- Motion Capture 动作捕捉

					- Strength

						- Realism can be high
						- capture large amounts of real data quickly

					- Weakness

						- Complex and costly set-ups
						- Capture animation may not meet artistic needs, requiring alterations

					- equip

						- Optical
						- Magnetic
						- Mechanical

					- Uncanny valley 恐怖谷效应

			- The Production Pipeline
			- Simulation

				- Single Particle Simulation

					- ODE, Ordinary Differential Equation 常微分方程

						- Euler's Method

							- aka Forward Euler, Explicit Euler
							- 速度、位置都用上一帧已知量计算
							- problem

								- unstable

									- 正反馈

								- Inaccuracies

									- solve

										- time step

							- theory

								- Solving by numeriacal integration with finite differebces leads two problems

									- Errors
									- Instability

						- define

							- stability

								- local truncation error(every step)
								- total accumulated error(overall)
								- orders w.r.t. step

						- Combat Instability

							- Midpoint Method / Modified Euler
							- Adaptive Step Size

								- 比较中点速度结果与欧拉结果决定是否缩减步长

							- Implicit Euler Method 隐式欧拉方法

								- 与欧拉方法不同

									- 使用下一帧的已知量计算

								- solve

									- root-finding algorithm
									- Newton' method

								- stability

									- order=1

										- local ~: O(h^2)
										- Global ~:O(h)

							- Runge-Kutta Families 龙格库塔方法

								- good at

									- Especially non-linearity

								- RK4

									- initial condition
									- solution

										- 

								- 数值分析

							- Position-Based / Verlet Integration

								- Idea

									- After modified Euler forward-step, constrain positions of particles to prevent divergent, unstable behavior
									- Use constrained positions to calculate velocity
									- Both of these ideas will dissipate energy, stabilize

								- pros/cons

									- Fast and simple
									- Not physically based, dissipates energy (error)

				- RigidBody Simulation

					- Similar to simulating a particle
					- just consider a bit more properties

						- positions
						- rotation angle
						- angular velocity
						- forces
						- torque 扭矩
						- momentum of inertia 转动惯量

				- Fluid Simulation

					- A Simple Positin-Based Method

						- assume

							- water

								- small rigibody spheres
								- can not be compressed / const density

						- So

							- density changes , "corrected" via changing the positions of particles

				- Eulerian vs. Lagrangian 欧拉法/网格法 vs. 拉格朗日法/质点法

					- Material Point Method ， MPM ，物质点法

						- 两种方法混合

		- Final project

			- Aesthetics 审美 is extremely important

	- GAMES202

		- Linqi Yan
		- Recap of CG

			- RenderPipeline

				- 不足

					- 全局光照

						- e.g.

							- 阴影

					- 间接光照

						- e.g.

							- 光线多次弹射

				- 好处

					- 直接光照

			- OpenGL

				- pros

					- cross-platform
					- dont care language
					- Alternatives

				- cons

					- fragmented：lots of different versions
					- debug

				- important analogy

					- Specify objects, camera, MVP

						- models

							- Model specification

								- VBO, Vertex buffer object

							- Model trabsformation

						- view

							- view transformation

					- Specify framebuffer and input/out textures

						- framebuffer

							- pass
							- MRT
							- 双缓冲

					- Specify vertex/fragment shaders

						- shading

							- VF shader

				- GLSL

			- The Rendering Equation

				- descirbe light transport
				- RTR, real time rendering

					- 

						-  outging lighting
						- incident lighting (from source)
						- (cosine-weighted) BRDF
						- visiblity

			- Environment Lighting

				- Representing incident lighting from all directions
				- cube map
				- sphere map

		- Real-time Shadows

			- shadow mapping

				- A 2-pass Algorithm 2步算法

					- The light pass shadow map 生成shadowmap
					- The Camera pass uses the SM (ShadowMap)

				- Pros

					- no geometry 不需要几何知识

				- Cons

					- 原因：shadow map 记录的深度与真实深度值有细微差别

						- grazing angle
						- 原因

							- shadowmap认为每一个像素点在场景中的深度是相同的

					- self occlusion 自遮挡

						- Add a variable bias to reduce self occlusion 增加深度偏移值

							- 问题：detach shadow issue 阴影不连续问题

								- e.g.

									- 脚底与阴影不连续

								- solve

									- bias调参

							- 调整遮挡判断

						- Second-depth shadow mapping

							- 取中间深度
							- 实质：使深度值更接近真实深度 

					- AA

						- 锯齿
						- solve

							- cascade
							- 动态分辨率shadowmap

				- FYI

					- RTR does not trust in COMPLEXITY

						- watertight

			- The math behind shadow mapping

				- 
				- 

					- Small support

						- point
						- directional lighting

					- smooth integrand

						- diffuse bsdf
						- constant radiance area lighting

					- e.g.

						- AO

			- PCSS, Percentage closer soft shadow

				- theory

					- PCF, Percentage Closer Filtering

						- AA
						- 求shadowmap 做（加权）均值滤波（每个像素周围区域）
						- 性能开销

				- Filter size

					- <->blocker distance
					- 

			- Basic filiter techniques
			- Distance Field Soft Shadows

				- pros

					- fast
					- high quality

				- cons

					- precomputation
					- heavy storage
					- articfact 瑕疵

				- Distance function

					- theory

						- Optimal Transport, 最优传输

				- Can Blend any two distance functions d1,d2
				- Usage

					- Ray Marching

						- Sphere tracing
						- Therefore， each time at p，just travel SDF(p) distance

					- soft shadow

						- determine the percentage of occlusion

					- Antialiased/infinite resolution characters in RTR

		- Real-time Environment Mapping
		- Real-time Global Illumination
		- Real-time PBR (Physical-based Material)
		- Real-time Ray-Tracing
		- A Solution

- 冯乐乐 Shader入门精要
- AP01-庄懂的技术美术入门课
- TA100-百人计划

	- 先行版
	- 美术

		- 美术理论

			- 1.1 美术理论基础

				- 光影

					- 黑白灰
					- 明暗五调子

						- 高光
						- 亮面
						- 灰面
						- 明暗交界线
						- 暗面

					- 常用词：飘

				- 透视

					- 透视类型

						- 平行透视/一点透视
						- 成角透视/两点透视
						- 三点透视
						- 散点透视
						- 鱼眼透视
						- 空气透视(/色彩透视/色调透视/影调透视/阶调透视)

					- 达芬奇的透视观点

						- 色彩透视
						- 消逝透视
						- 线透视

				- 色彩

					- 三要素

						- 色相
						- 纯度

							- 饱和度
							- 灰度
							- 例子：这颜色不够纯

						- 明度

							- 例子：颜色有点脏了

					- 三原色

						- 光学RGB
						- 颜料CMY

					- 其他定义

						- 间色
						- 复色
						- 同类色
						- 互补色
						- 对比色
						- 色性：冷暖色

				- 构图

					- 形式

						- 水平式：安定有力感
						- 垂直式：严肃端庄
						- S形：优雅有变化
						- 三角形

							- 正三角较空
							- 锐角刺激

						- 长方形：人工化有较强和谐感
						- 圆形：饱和有张力
						- 辐射：有纵深感
						- 中心式：主题明确，效果强烈
						- 渐次型：有韵律感
						- 散点式：自由可向外发展

				- 镜头语言

					- 蒙太奇
					- 常用手法

						- 拉
						- 移
						- 跟拍
						- 摇

							- 旋转

						- 升降镜头
						- 推

				- 美术风格

					- 常见分类：东方西方卡通写实

				- 常用语

					- 脏
					- 乱
					- 散
					- 飘
					- 纯

			- 角色设计精要

				- 流程

					- 确定方向
					- 寻找参考，细化需求
					- 设计原型
					- 迭代

				- 精炼

					- 确定角色关键词

						- 特点

							- 独一无二

						- 关键词

							- 世界观
							- 背景
							- 能力
							- 职业
							- 性格
							- 喜好

					- 收集素材和灵感
					- 构图设计

						- 图形感

							- 轮廓剪影
							- 内在构成

								- 点
								- 线
								- 面
								- 比重

									- 疏密
									- 轻重
									- 松紧

						- 构图元素

					- 配色
					- 服装设计

			- 场景设计精要

				- 主题设定

					- 常见

						- 剑侠
						- 科幻
						- 废墟
						- 魔幻

				- 场景风格确定

					- 写实
					- 非写实

						- 赛博朋克
						- 卡通
						- 像素地面数

				- 场景设计构图

					- 构图法

						- 三分
						- 环形
						- 对称
						- 垂直线
						- 水平线分割
						- 十字分割
						- 视觉引导

					- 剪影

						- 原则

							- 统一中求变化
							- 辨识度

						- 常见问题

							- 杂乱无章
							- 变化单一

								- 没有节奏
								- 没有疏密

						- 改善

							- 整点时钟分析

					- 剪影内切
					- 剪影空间处理

						- 视觉中心
						- 突出部

				- 前景场景和纵深感
				- 场景配色

					- 配色比例

						- 日本设计配色黄金比70:25:5

							- 主色

								- 常为深色/饱和度高色

							- 辅助色

								- 同类或者邻近色/互补色/中性色黑白灰

							- 点缀色

								- 饱和度高或者明度高

						- 一般不建议超3种

					- 色彩关系
					- 色彩搭配

						- 相邻色
						- 间隔色
						- 互补色

					- 叠色

						- 起稿子

							- 灰度

						- 铺调子

							- 上色

						- 设计和塑造

					- 分类

						- 亮色

							- 休闲游戏

						- 暗色

							- 核心游戏

				- 场景光影氛围

					- 打光

						- 顶光
						- 自然光
						- 自发光

					- 光影分割

				- 场景细节添加

		- 建模原理

			- DCC工具链

				- 建模

					- 3dmax

						- 硬表面建模
						- 静态物体建模

					- maya

						- 动作向TA
						- 效果向TA

					- Houdini
					- Blender

				- 贴图

					- Substance

						- sp
						- sd

							- daniel thiger

						- alchemist

					- marry
					- quixel mixer

				- 常用

					- ps
					- rizom uv

						- 拆UV

					- BANJIAJIA 渲梦工厂

						- 工具向TA

			- 模型基础

				- 阶段

					- 模型
					- 贴图

						- 八猴
						- SP

					- 渲染

						- 离线

							- Arnold for c4d

								- 无偏
								- 精致漂亮
								- 人物
								- gpu渲染

							- vary for max

								- 有偏
								- 快

						- 实时

							- 八猴
							- UE4
							- Unity

				- 次时代流程

					- 与传统手绘流程区别

						- 法线的引入

					- 阶段

						- 中模

							- 输入：原画
							- 高模卡线之前

						- 高模

							- 工具：ZB

						- 拓扑

							- zb
							- maya

						- 低模

							- 匹配度
							- 布料解算

						- 拆UV

							- Unfold3d

						- 烘培贴图

							- 八猴
							- SP

						- 制作材质

							- SP
							- PBR流程

						- 渲染输出

				- 角色

					- 基本人体
					- 人头
					- 装备
					- 头发基本体
					- 细化

						- 人头
						- 装备

					- 贴图
					- 环境测试
					- 输出

				- 硬表面
				- 灯光测试
				- 注意

					- TA作品
					- 体现流程

			- 硬表面基础

				- 定义

					- 工业制成品

				- 卡倒角

					- 卡线

						- 光滑组
						- 软硬边

					- 面

				- 烘培法线

			- 常见模型规范（次时代）

				- 布线合理性

					- 基本

						- 均匀
						- 关节处多
						- 线数量把控

							- 尽量使用在剪影上

					- 多星点问题

						- 多星点：超过四条边的顶点
						- 缺点

							- 导致突起
							- 影响法线

					- 预连接问题

						- 软件差异性
						- 三角形预划分

				- UV合理性

					- 传统

						- 01框
						- 一个材质球一个uv一张贴图

					- udim：多象限

						- sp

							- 导入时设置
							- 实质上把每个象限uv分成多个材质球

					- 注意点

						- 提高单张uv利用率

							- 打直
							- 不能有不均匀拉伸

						- 公用UV除了1块外移出01框
						- 硬边UV必须断开
						- Tiling贴图左右对齐

				- 光滑组/软硬边

					- 影响法线

						- 硬边uv断开原因：否则一个顶点有多条法线

					- 平台差异

						- maya：软硬边
						- max：光滑组
						- 导出时解锁法线

				- 递交检查
				- 常见问题

					- SP导入出错

						- 01框问题

					- maya与max互导

						- 法线锁定
						- 场景设置长度基本单位

				- 制定规范

					- 表格形式
					- 配图
					- 回收检验

			- 美术流程

				- 传统流程
				- PBR流程

					- Metallic与Specular流程

						- 次时代

							- 高低模烘培
							- PBR贴图

						- 共有贴图

							- Normal map
							- Height map
							- AO

						- 特有贴图

							- Metallic/Roughness流程

								- base color

									- sRGB

										- 金属

											- 漫反射颜色

										- 非金属

											- F0值 Reflectance value

									- 不含光照，除了Micro-occlusion
									- 颜色约束

										- 非金属

											- 30/50-240 sRGB

										- 金属

											- 180-255 sRGB

												- 原因：70-100%的镜面反射

								- Metallic

									- 信息

										- 金属度
										- 灰度

									- 作用

										- 解读BaseColor

											- 0.0：非金属
											- 1.0：纯金属

									- 定义

										- 灰阶：不同程度的氧化和污垢
										- 金属被氧化，腐蚀，上漆，覆尘需要被当作非金属看待
										- 如果Metallic贴图有低于235 sRGB，则BaseColor中对应反射值也应该降低

								- Roughness

									- 信息

										- 粗糙度
										- 灰度

									- 解读

										- 0.0：平滑
										- 1.0：粗糙

							- Specular/Glossiness流程

								- Diffuse

									- sRGB

										- 金属

											- 0.0

									- 不含光照，除了Micro-occlusion
									- 颜色约束

										- 30/50-240 sRGB

								- Specular

									- F0

										- 0度Fresnel反射值
										- sRGB

											- 非金属：40-75 sRGB

												- =2-5%反射值
												- 液体

													- 0.02-0.04反射值（线性空间）

											- 宝石

												- 0.05-0.17反射值（线性空间）

											- 原始金属：180-255 sRGB

												- =70-100%反射值

									- 问题

										- 能量守恒

											- 反常数值：1.0漫反射+1.0镜面反射>原金属度光线

										- 线性空间与sRGB转换

									- 规范

										- 假设未记录材质F0为4%（塑料）

								- Glossiness

									- 灰度

										- 0.0：粗糙
										- 1.0：平滑

						- 问题

							- 贴图分辨率与纹素密度过小时，金属导体与非金属交接会产生白/黑边

								- 解决：良好布局和大小的UV

						- 两流程对比
						- 流程转换

							- M->S

								- BaseColor+Metallic->Diffuse
								- BaseColor+Metallic->Specular
								- Roughness->Glossiness

									- 反向

							- S->M

								- Diffuse+Specular->BaseColor+Mataliic
								- Glossiness->Roughness

									- 反向

							- 工具

								- SD（建议）

									- SD检查：PBR BaseColor / Metallic Validate节点

								- Ps

									- 常见问题

										- Ps中混合处理会被自动转换到Gamma空间

					- 生产

						- 法线贴图的生产

							- 高低模烘培
							- 存储

								- 法线空间
								- 切线空间

									- 可压缩

										- 根据两个值推算第三个值

									- 可重用
									- 存储相对信息

										- 使用时Unpack

							- DCC软件计算
							- 问题处理

								- 法线反相

									- 材质赋予出错
									- 模型处理时注意uv

						- 流程

				- UV原理

			- uv原理

				- uvw展开

					- 非破坏性
					- 优势

						- 灵活

				- 展开方式

					- 快速投影映射

						- 缺点

							- 作用有限

								- 适用于重复纹理

							- 重叠

						- 快速投影于标准几何形状

							- plane
							- cube
							- Cylinder

					- 手动展开

						- 均匀性要求
						- 空间利用
						- 分割数量

					- 自动展开

						- 问题

							- 质量
							- 一般与手动配合

					- 重叠uv展开

						- 对称纹理
						- 简单重复纹理
						- 重复复制模型

				- 规范与要求

					- 扩边值/溢边值

						- 512-2像素
						- 1024-4
						- 2048-6/8

					- 打直
					- 间隔4-8个像素
					- 一般不允许倒放，除非极大程度提高利用率
					- 同材质尽量相邻
					- 断开uv必须相邻，接线保持一致
					- 2通道光影uv不允许翻转叠放，一定程度上允许拉伸

				- uv通道

					- 默认一套
					- 导入设置Generate Lightmap UVs

						- 光照贴图：uv1
						- 动态光照：uv2

					- 优点

						- 多uv可以代替很多mask以增加性能

					- 缺点

						- 增大model体积

					- 格式差异

						- fbx：多
						- obj：一
						- unity：8

				- 光照uv

					- 可以低精度
					- 不允许重叠

				- 软件

					- unfold3D
					- RizomUV

			- 资源规范基本说明

				- 命名与存储

					- 贴图

						- 分类

							- 角色
							- 特效
							- 环境
							- 物体
							- UI
							- RendererTarget
							- 其他

				- DCC标准光照环境搭建
				- 材质规范

					- 材质参数

						- 定死，方便合批

					- 混合模式

						- 不透明>Mask>半透明
						- 性能考虑
						- 半透明问题解决

							- 手动排序

					- 植被

						- 树叶

							- 不烘培光照

						- 草

							- 不烘培光照
							- 法线向上特殊shader+AO

						- 树

							- 球形法线
							- 特殊shader+AO

						- 缺点

							- 烘培面积影响内存
							- 建议不烘培，使用shader

				- 贴图

					- 动态物体

						- 采样

							- 3 pbr + 1 shadowmap

						- 大小

							- Albedo

								- 2048/1024

							- normal+smoothness

								- 1024

							- AO+metallic+其他

								- 512

					- 静态物体

						- 采样

							- 2pbr + shadowmap + 烘培shadowmap

						- 大小

							- Albedo

								- 2048
								- rgba

							- normal+smoothness

								- 2048

							- AO+metallic+其他

								- 1024

							- shadowmap

								- 2048

					- 规范

						- Albedo:RGB (+opacity:A) 
						- normal (RG)+smoothness(B)

							- 法线由RG通道推B通道

						- AO (R)+ metallic (B)
						- .tga

				- 逻辑模块化
				- 注意

					- （各DCC软件）引擎标准光照环境搭建

						- 光照差别
						- 曝光差别
						- shader差别
						- 后期差别
						- 贴图差别

		- 动画基础

			- 动作理论

				- 动画原理

					- 动画十二法则
					- 动画师生存手册

				- 基础知识

					- 运动/变换 translation
					- 蒙皮 skinning

						- LBS, linear Blend Skinning, 线性混合蒙皮

							- 问题

								- 弯曲和扭曲处变形

						- DQS, Dual Quaternion SKinning，双四元数蒙皮

							- 游戏引擎一般不支持
							- 关节膨胀
							- eg

								- DAZ

						- LBS问题的解决

							- JCM, Joint Controlled Morphs，骨骼驱动变形

								- maya: PSD, Pose space deformations
								- morphs变形
								- eg

									- Metahuman

							- RBF, Radial Basis Function, 辅助骨骼驱动

								- 解决JCM的Morphs消耗

							- RTSS, Real-time Skeletal Skinning，基于优化旋转的实时骨骼蒙皮

					- 动画类型

						- 逐帧动画
						- 骨骼动画

							- 2D
							- 3D

						- 顶点动画

							- 离线

								- mmd，houdini布料
								- ue渲染

							- 实时

								- shader

				- 质量与流畅度

					- FK、IK

						- FK
						- IK

							- 实时运算

					- 流畅度和弧线

						- 运动轨迹
						- 运动规律

					- 打击感-动作

						- 合理打击反馈

							- eg

								- 格斗游戏

							- 抽帧

								- 受击停顿

							- 顿帧

								- 击打震动

						- 预备和缓冲

							- 前摇和后摇

						- 攻击节奏和按键反馈

							- 节奏

								- 待机
								- 蓄力
								- 攻击
								- 收招

					- 夸张

						- 挤压与拉伸
						- 拖尾与变形，运动模糊

							- eg

								- OBAKE

						- 不正确的透视

					- 时间操纵

				- 动画表现提升

					- 表情

						- 写实
						- 欧美卡通
						- 日式卡通

					- 视线切换
					- 闭眼高光
					- 交互体验
					- 穿模

						- IK

					- 动作状态融合

						- ALS

							- 动作叠加
							- 分层融合

						- 连招
						- 停止

			- 2D动画-Spine

				- 时间与空间

					- 动画方法

						- 逐帧画法
						- 原动画法
						- 结合

				- IK和FK
				- 2D骨骼动画

					- PS人物切片
					- 创建网格
					- 骨骼绘制
					- 骨骼绑定

						- 绑定网络
						- 父子关系
						- IK约束

					- 面部绑定

						- 与头部的反向约束

					- 制作动画
					- 导出

			- 3D动画

				- max

					- 常用骨骼类型

						- Bone
						- CS, character studio
						- CAT, Character Animation Toolkit

					- 蒙皮

						- Skino

					- IK，FK

						- IK解算器

					- 控制器绑定

						- 约束

							- 附着
							- 位置
							- 曲面
							- 链接
							- 注视

					- 插件

						- bones pro
						- InstantRig
						- weightPro
						- IKMax For 3DS Max Released

				- maya

					- 基础概念

						- 教程：Animator Friendly Rigging
						- 绑定

							- 层级
							- 骨骼

								- FK
								- IK

							- 蒙皮
							- 约束
							- 变形器

								- deform
								- BlendShape

									- 表情
									- 修形

					- 制作

						- 绑定规范

							- 模型规范
							- 流程规范
							- 文件层级命名规范
							- 效果规范
							- 其他规范

						- 插件

							- AdvanceSkeleton
							- mGear

								- free

							- 萌芽表情绑定工具
							- 劲爆羊工具盒

						- 表情制作

							- 动画

								- 骨骼
								- blendshape

							- 游戏

								- 动作捕捉
								- blendshape

				- blender

			- 动作流程规范

				- 检查模型

					- 单位
					- 中线

						- 模型中线与max中线必须重合

					- 布线

						- 关节

							- 凸三凹二

					- 坐标

						- xform坐标归0

					- 隐藏

						- 检查隐藏内容
						- 点、线、面、元素 显隐

					- 法线、光滑组、合并点

				- 搭建骨骼

					- 骨骼层级
					- dummy/虚拟体不能做根骨骼
					- IK动画

						- 烘培
						- 塌陷
						- 隐藏虚拟体

					- 武器换手

						- 武器缩放

							- 资源消耗

						- prop骨骼

							- unity设置根骨骼为质心

					- 扭曲链接

						- unity的humanoid不支持

					- 挂点

						- 常用
						- 坐骑

							- dummy虚拟体
							- 父子链接

					- 坐标轴对齐
					- 镜像问题

						- 不建议

					- 保存蒙皮姿势

				- 蒙皮设置

					- 权重受控数

						- unity：4

					- 换装蒙皮接缝

						- 权重设1

					- root bone问题

						- 必须设置根骨骼权重
						- 导出fbx过滤权重为0骨骼

				- 动画制作

					- bone on

						- 父子级别bone子级关闭bone on

					- CS骨骼缩放继承

				- 导出

					- 烘培

						- IK
						- link
						- 路径动画
						- 其他非常规动画

					- 曲线过滤
					- 层动画塌陷
					- 导出所选
					- 命名

				- 其他

					- 粒子视图问题
					- 命名与路径

						- 空格
						- 一致性

					- 动画命名：模型名@动作名

						- @关键字自动化动作名称

			- BlendShape

				- 应用

					- 表情

						- 表情捕捉

					- 其他形变效果

				- 概念

					- MorphTargets/混合变形/Shape Keys/变形器/Morpher
					- 骨骼级别下的Mesh变形器

						- 顶点（数量及顺序）相同

					- 实质：数学线性插值
					- BlendShape间可叠加

				- 制作

					- max

						- 变形器

					- maya

						- 形变编辑器

				- 使用

					- unity

						- script

							- skinnedMeshRenderer.SetBlendShapeWeight(int index,float weight)
							- skinnedMeshRenderer.GetBlendShapeWeight(int index,float weight)
							- skinnedMeshRenderer.GetBlendShapeWeight(string Name)

						- Animation动画

				- 缺点

					- 性能消耗
					- 模型定点顺序影响渲染顺序

						- eg

							- 透明排序

			- Animate系统

				- unity

					- Animator

						- Apply root node
						- controller

							- BlendTree
							- layer

					- Animation
					- 导入动画注意事项

		- 特效美术

			- 特效理论

				- 平面构成

					- 点

						- 定位视点

							- 黄金分割

						- 增加细节

					- 线

						- 疏密
						- 轨迹和力
						- 动静

					- 面

						- 形状
						- 融解度

							- 风格化

				- 结构
				- 光影

					- 亮度

						- 对比
						- 学科范围

							- UI
							- 角色
							- 环境
							- VFX

					- 色彩

				- 节奏

					- 间隔
					- 重复
					- 节拍

				- 对比

					- 大小
					- 疏密
					- 远近/透视
					- 色相

						- 点缀色

			- 2D

				- 工具

					- spine

						- 动作与特效结合

					- live2d

						- 卡牌立绘

				- 实质

					- 帧动画

				- 技能特效

					- 出现
					- 飞行
					- 击中
					- 消散

				- 绘制拆分

					- 三个状态
					- 自动补帧

				- 骨骼绑定
				- 颜色变化

					- mask

				- 岗位要求

					- 动画
					- 原画

				- 缺点

					- 粒子特效

				- 工具

					- EffectHub

			- 优化

				- 理论

					- overdraw
					- drawcall
					- 带宽

						- 贴图读取
						- 内存加载

							- e.g.

								- AssetBundle
								- Resource

				- 具体操作

					- 模型

						- 制作标准

							- 面数

								- 500
								- 1000+lod

							- 骨骼

								- 30+lod

							- 避免mesh collider
							- 导出

								- 坐标归0
								- 不烘培动画
								- 检查法线
								- 合并顶点
								- 清除一切没用的东西

									- 场景
									- 多余材质球

						- 合并与裁剪

							- 合并

								- drawcall

							- 裁剪

								- 透明区域

					- 贴图

						- 制作标准

							- 2的n次幂

								- 512

							- 正方形纹理

								- 有效利用内存

							- 合并简单常用特效到一张图，通过偏移UV采样

								- 减少内存

									- 材质数量

							- 通道相关

								- 减少使用Alpha通道
								- 一张图的多个通道存储多个灰度图
								- 灰度图

									- png

								- rgba

									- tga

							- 程序化shader

								- 采样消耗大于计算
								- 规则图形

							- 关闭mipmap

								- 空间占用

						- 合并

							- 同一位置
							- 纹理运动相同
							- 节省资源

					- overdraw

						- 原理

							- 透明物体没有遮挡剔除
							- 重复绘制

						- 方法

							- 透明材质

								- CutOff

							- 堆叠

						- 粒子特效

							- 制作标准

								- Emitter最大数量根据lod
								- 尽量不发射复杂模型
								- Scaling Mode->Hierachy

									- 避免缩放显示问题
									- 提高缩放情况下的复用

								- 调整Max Palticles

									- 根据当前粒子最高峰值

								- 谨慎使用Noise类功能

							- 优化

								- 善用速度减少生成数量

			- 规范与拆分

				- 规范

					- 项目结构

						- resource

							- ui
							- other

						- prefab

					- 资源

						- 贴图

							- 2^n
							- 1024*1024
							- minmap
							- 格式

								- png
								- tga

							- 总数

								- 通用性

							- 填充率

								- overdraw

							- 分类

								- 排除相近和相似

						- 模型

							- 面数

								- 500-

							- 总数
							- mesh read/write
							- 输出

								- 关闭不需要的项

									- 动画
									- 灯光
									- 贴图

					- 命名
					- 制作

						- 粒子发射器

							- 复杂
							- 数量

						- Batches

							- 实质：drawcall
							- 材质球复用

						- overdraw

							- 重叠

						- 关闭不需要的选项

							- 阴影
							- 受光

						- order in layer / RenderQueue

							- 合批规则相关

				- 调用

					- 技能编辑器

						- 由模型、动作、特效组合
						- 编程

					- 代码调用

						- prefab
						- 路径

				- 特效分级

					- 根据平台/设备划分

						- 高
						- 中
						- 低

					- 根据分级确定具体数值

		- 灯光色彩

			- 基础灯光

				- 平行光
				- 点光源
				- 聚光灯
				- 区域光

					- 烘培

				- 自发光
				- 环境光

					- cubemap

			- 反射与阴影

				- 宏观

					- 漫反射
					- 镜面反射

				- 阴影

					- 分类

						- 漫反射阴影/环境光遮蔽AO
						- 直接光阴影

					- 美术

						- 软阴影
						- 硬阴影

			- 光照与色彩

				- 色温

					- 固体加热符合色温定律
					- 日常生活中见不到黑体辐射为蓝色

						- 太阳（3600k）黑体辐射为白色
						- 恒星（温度10000k+）黑体辐射才能为蓝色

					- 气体燃烧不符合色温定律

				- 明度/饱和度

					- 物体表面颜色=直接反射光（白色）+物体吸收后反射光原色（固定值）
					- 超过上限的所有光原色都会反射，与没超过上限的反射光色混合
					- 物体表面颜色明度上升，饱和度降低

				- 色相

					- 白光不会引起色相变化

				- 天空色彩原理

					- 光波波长
					- 大气厚度/大气层大气分子

				- 色彩应用

					- 固体色温定律
					- 补光颜色与明度饱和度变化

			- 视觉与色彩

				- 色彩补偿

					- 视觉残像

						- 高饱和色引起视觉疲劳，互补色感光细胞受抑制
						- 刺激停止后该色互补色感光细胞开始活跃产生颜色

					- 同时性效果

						- 互补色效果增强

					- 互补色平衡理论

		- DCC

			- SD

				- 阶段

					- 颜色

						- 运算
						- 灰度映射

					- 高度
					- 函数

						- FxMap

				- 常用节点

					- SVG

						- 钢笔工具
						- 矢量图案

	- 程序

		- 一、渲染基础

			- 一、渲染流水线
			- 二、向量

				- 1.向量

					- a.基本运算

				- 2.矩阵

					- 意义

						- 数学意义：线性方程组

					- 增广矩阵化简：

						- （将系数矩阵变换为单位矩阵）
						- 几何意义：将不规则矩阵空间变换为笛卡尔空间下的点（值矩阵）的位置

					- 列空间

						- 每一列表示该矩阵空间下的单位向量

					- 运算

						- a.矩阵乘法

							- 几个重要的~：

								- 缩放
								- 斜切/切变
								- 旋转（手推）
								- y=x对称
								- 平移（仿射）

						- b.转置

							- 现实意义/原因：一些软件中矩阵是以列优先方式进行存储，所以使用转置将逻辑变换为行优先（一般逻辑）

						- c.逆

			- 三、MVP变换
			- 四、纹理
			- 五、平台图形API（硬件）

				- 1.定义

					- 应用端
					- 图元
					- 纹理

						- 纹素

					- 顶点数组
					- 顶点缓冲区
					- 顶点着色器
					- 片元着色器

				- 2.DirectX、OpenGL、OpenGL ES

					- OpenGL

						- Win、Mac、Unix/Linux
						- Khronos Open Standards for Graphics and Compute
						- OpenGL 1.0、OpenGL 2.0、OpenGL ES 1.1、OpenGL ES 2.0 关系

					- DirectX

						- Win

					- OpenGL ES

						- 兼容性：向后兼容
						- 3.0新特性
						- 渲染关键

							- 移除AlphaTest
							- 移除LogicOp

								- 很少使用

				- 骁龙Adreno对应OpenGL ES

		- 二、Shader基础

			- 一、色彩空间

				- 原理

					- 成色原理
					- 可见光波长
					- 能量分布/光波

						- 分光光度计
						- 功率

				- 定义

					- 色彩三角形

						- 在色度图上的一个三角形部分

					- 色域马蹄图

						- Y：亮度
						- xy：色度

				- 指标

					- 色域

						- 三基色坐标

					- Gamma

						- 色彩三角形切分方法

					- 白点

						- 重心位置

				- HDR
				- sRGB

					- 微软惠普发布的颜色空间标准

				- Gamma

			- 二、模型与材质

				- uv

					- 片段着色器
					- 模型uv

						- SP、Ps制作贴图

				- 模型

					- OBJ文件

						- V
						- Vt:uv
						- VN:normal

					- FBX

						- 顶点色
						- lod
						- 多uv

				- 材质
				- 插值与重心坐标
				- 法线

					- 面法线
					- 顶点法线

						- 光滑组
						- 法线偏移

			- 三、常用函数

				- ret=frexp(x,out exp)

					- 浮点数

						- ret：尾数
						- exp：指数

				- 双曲函数
				- 光线运算

					- lit()
					- faceforward()

				- 纹理查找

					- tex*D(s,t)
					- tex*Dlod(s,t)
					- tex*Dbias(s,t)
					- tex*Dgrad(s,t,ddx,ddy)

						- ddx,ddy，偏导数，计算决定mipmap层级

					- tex*Dproj(s,t)

			- 四、传统经验光照模型

				- 经验模型

					- Phong和Blinn-Phong的本质区别

						- Phong没有顾及viewDir和lightDir在normal同侧的效果

							- 当reflectDir和viewDir超过90度时，Phong将截断负值到0

					- Goround模型

						- 计算光照仅在顶点阶段，片元阶段做插值

					- Flat模型

						- 每个面只有一个颜色

				- PBR

			- Bump图

				- BumpMapping
				- 应用

					- NormalMapping
					- ParallaxMapping 视差

						- 遮挡关系
						- 高度图

							- 顶点位移
							- 原理

								- 高度图采样纹理进行偏移

						- Steep Parallax Mapping 陡峭视差映射

					- ReliefMapping 浮雕

						- 原理

							- 视差步进
							- 二分查找

						- 视差闭塞贴图 pom

							- 视差步进
							- 插值

				- 压缩格式

					- 非移动平台

						- DXRT5nm

							- 原理：切线空间

								- 切线，副切线

							- 只此处两个通道(G,A)

					- 移动平台

						- RGB

			- Gamma矫正

				- 对线性三色值和非线性视频信号的编码和解码
				- 传递函数

					- OETF光转电
					- EOTF电转光

				- 由来

					- 计算机用更多的位数去存储暗部信息

						- 人眼对暗部变化更加敏感
						- 真彩色RGB32

							- 每个颜色通道只有8位

					- CRT显示器颜色的非线性显示的历史原因

				- gamma(sRGB)=2.2
				- 线性工作流与Gamma工作流
				- 硬件支持

					- Unity

						- sRGB Frame Buffer
						- sRGB Sampler

					- SP

						- sRGB设置

					- PS

						- 设置灰度系数为1
						- 半透明设置：用灰度系数混合RGB

				- 代码矫正

			- HDR

				- DR=最高亮度/最低亮度
				- 区别

					- LDR

						- 8精度
						- 0-1单通道
						- 格式

							- jpg
							- png

					- HDR

						- 格式

							- hdr
							- tif
							- exr
							- raw

				- 缺点

					- 渲染速度慢，需要更多显存
					- 不支持硬件抗锯齿
					- 需要硬件支持

				- 相机中的HDR转LDR

					- 计算曝光
					- 输出线性值
					- LUT变化

						- 白平衡
						- 色彩校正
						- 色调映射
						- 伽马校正

				- Bloom

					- 需要HDR中超过1的值
					- 原理

						- 理论

							- 计算高光像素
							- 高斯模糊
							- 叠加

						- UnityBloom原理

				- ToneMapping：HDR->LDR

					- 线性映射

						- 效果差

					- S形曲线

						- ACES

				- LUT

					- 对LDR画面滤镜

			- flowmap

				- flow map

					- 2D向量信息的纹理
					- RG通道

				- 平台差异

					- ue

						- 反转了G通道

					- unity

				- 优点

					- 廉价高效

				- 应用

					- 熔岩流动
					- 天空球

		- 三、渲染应用

			- 透明度测试
			- 模板测试 Stencil Test

				- 原理

					- color buffer
					- stencil buffer 模板缓存

						- 比较
						- 更新

					- After stencil test

						- Pass

							- PassBack
							- PassFront

						- Fail

							- FailBack

						- ZFail

				- 参数

					- StencilBufferValue
					- referenceValue

				- Op
				- 应用

					- 描边
					- 多边形填充
					- 反射控制
					- shadow volume阴影渲染

				- 注意

					- 美术功底

			- 深度测试 Ztest

				- 原理

					- framebuffer
					- 画家算法
					- ZBuffer算法

				- 技术

					- early-z

						- vert与frag之间
						- ZTest (z-cull)
						- 减少无用计算

					- ZTest (z-check)

						- frag之后
						- 确保结果正确

				- 参数

					- 深度值ZBufferValue
					- refrenceValue

				- 问题

					- 深度冲突

						- 原因：深度缓冲区精度为浮点值
						- 两物体距离太近导致视觉上交替出现
						- 防止

							- 距离
							- 精度
							- 拉远近平面

						- Unity

							- Offset

				- Op

					- ZWrite

						- 开启写深度缓冲

					- ZTest

						- 通过写颜色缓冲
						- 不通过

							- 关闭ZWrite

				- 渲染

					- 多Psss

						- Queue

							- 选取Pass中最靠前的Queue

						- Pass顺序

							- 按照编写顺序依次执行

					- 顺序

						- 不透明：前->后
						- 透明：后->前

				- 应用

					- 深度着色
					- 阴影贴图 ShadowMap
					- 透明、粒子渲染
					- X-Ray
					- 切边
					- 护盾

				- 注意

					- 色彩搭配

			- 曲面细分和几何着色器

				- 曲面细分

					- 应用

						- 雪地
						- 海浪

				- 几何着色器

					- 应用

						- 草地
						- 几何动画

			- 延迟渲染管线

				- 渲染管线

					- 定义

						- 光照的实现方式

					- 方式

						- forward
						- defered
						- forward+

				- 前向渲染

					- 每个物体都对Unity设置的最近n个光源进行考虑

				- 延迟渲染

					- 解决大量光照渲染方案
					- 方法

						- 把光照计算延迟到G-Buffer阶段进行计算

							- G-Buffer 深度测试

								- RT

							- frag阶段只计算顶点色不关心关照

						- 透明物体使用前向渲染

					- 实质

						- 对G-buffer中RT的2D光照后处理

					- 优劣

						- 优

							- 大量光照场景优势

								- 光源数量对计算复杂度无关

							- 后处理支持良好

								- 深度图直接G-Buffer拿来使用
								- 前向渲染需要额外计算深度图

							- 节省计算量

								- 只计算可见像素

						- 劣

							- MSAA抗锯齿不友好
							- 透明物体渲染问题
							- 占用大量显存
							- 不支持自定义个性化光照计算

								- 原理：延迟渲染使用LightPass计算光照

					- 移动端优化

						- TBDR

							- 通过分块降低带宽

						- TBDR

							- 基于手机GPU的TBR架构通过HSR(可见性测试)减少overdraw

					- 与前向渲染区别

						- 后处理
						- 着色计算
						- 抗锯齿方式

					- 应用

						- 主机项目
						- 源神

				- 延迟光照

					- 着色计算使用Forward
					- 更少的G-Buffer
					- 支持多种光照模型

				- Forward+

					- 原理

						- 分块索引正向渲染
						- 存储深度和法线信息
						- 强制需要preZ深度预计算渲染RT

					- 减少带宽
					- 支持多光源
					- 对单独的深度和法线信息进行单独后处理

				- 群组渲染

			- 优化原理

				- early-z 和 preZ

					- early-z

						- 深度测试带来的问题

							- 有大量片元计算后没通过测试被抛弃

						- 可以搭配模版测试
						- 失效

							- 1

								- Alpha Test
								- clip
								- discard

							- 手动修改GPU深度
							- Alpha Blend

								- ZWrite Off

							- Depth Test Off

						- 基于硬件
						- 问题

							- overdraw

					- Zprepass

						- 解决early-z对透明的问题
						- 双pass法

							- 无法动态批处理
							- DrawCall问题

						- 提前分离Prepass

							- 先使用一个shader计算深度RT
							- 其他原shader

						- 计算消耗

					- 应用

						- 毛发渲染

				- 纹理压缩

					- 纹理格式与图片格式

						- 纹理格式：显卡直接处理的格式

					- 纹理管线

						- 如果不设置纹理压缩格式，将进行CPU压缩RGBA32，增加了CPU时间和带宽

					- 格式

						- DXTC

							- DXT1

								- 压缩比：6:1

							- DXT2/3

								- 压缩比：4:1

							- DXT4/5

								- 压缩比：4:1

						- ATI1/2 (BC4/BC5)

							- 压缩比：4:1

						- BC6/BC7

							- BC6

								- HDR
								- 压缩比：6:1

							- BC7

								- 压缩比：3:1

						- ETC

							- android
							- ETC2

								- 主持alpha
								- 硬件要求opengl es3.0和opengl 4.3

						- ASTC

							- HDR/LDR
							- 压缩比：4~36:1
							- Android 5.0 / openGL ES 3.1
							- iphone6

						- PVRTC

							- Iphone/Ipad
							- 部分安卓
							- 压缩比：6:1

					- 画质：RGBA>ASTC 4*4>ASTC 6*6>ETC2≈ETC1
					- 建议

						- PC

							- 低质量

								- rgb：DXT1
								- rgba：DXT5

							- 高质量

								- rgba：BC7

						- android

							- 低质量

								- rgb：ETC1
								- rgba：ETC2

							- 高质量

								- ASTC

						- ios

							- 低质量

								- PVRTC2

							- 高质量

								- ASTC

					- 常用

						- mipmap
						- 常用ASTC

			- GPU架构

				- 移动GPU框架TB(D)R

					- Tile-Based（Deferred）Rendering 屏幕分块渲染

						- 整个屏幕分成像素n*n的小块

					- 核心目的

						- 降低带宽，减少功耗

					- Defer

						- 阻塞+批处理 GPU的1帧的数据
						- 阶段

							- Binning / 批处理

								- 几何处理逐生成tile-图元列表

							- early-DT

								- 逐块光栅化及后续处理

					- 优点

						- 消除Overdraw
						- cached friendly

					- 缺点

						- binning性能瓶颈
						- 某些三角形在多个tile上，需要被绘制多次

					- 其他

						- IMR

							- 立即模式渲染
							- PC端

					- 优化

						- Framebuffer clear/discard
						- 减少tile buffer和system memory交互
						- 图片

							- 压缩 ASTC、ETC2
							- mipmap

						- 避免frag动态计算uv
						- 延迟渲染尽量利用Tile Buffer
						- 带宽的考虑
						- 少用discard打断early-DT
						- float和half区分
						- 避免曲面细分，置换贴图

					- 缺点

						- 深度图

							- 使用时将重新渲染画面数据

				- PC端 GPU架构  NVIDIA GPU Architecture

					- 渲染运行机制

						- SIMD和SIMT

							- Single Instruction Multiple Data
							- Single Instruction Multiple Threads
							- co-issue

								- 解决SIMD中运算单元无法充分利用
								- 将1D与3D或2*2D的数据合并成1个4D进行计算
								- 一个数据既是运算又是存储则无法启用

									- x=x+y，如x

					- 异构系统

						- 分离式
						- 耦合式

							- 游戏主机

					- 资源机制

						- shader访问临时缓冲区L1，L2很快
						- shader访问纹理，常量缓存和全局内存有非常高延迟

							- 纹理

								- cache-missing

									- 纹理命中率

						- 原理：寄存器物理位置
						- shader在GPU硬件运行机制

					- 优化建议

						- 自定义几何实例化代替unity原生合批

							- 静态合批增加vbo内容占用
							- 动态合批增加cpu耗时开销

						- 减少顶点数与三角面数

							- 顶点数

								- 减少vert()运算
								- 减少gpu中framebuffer存储

							- 三角面数

								- 减少frag()运算

						- 避免每帧提交buffer数据

							- unity

								- 粒子系统运算从cpu端改到gpu端
								- 避免透明粒子特效

									- 造成严重overdraw

						- 减少渲染状态的设置与获取

							- 避免update设置material

						- 3D使用LOD，开启mipmap

							- lod减少顶点与面消耗
							- mipmap减少cache-missing

						- 避免alphatest

							- early-z失效

						- 避免三角面过小

							- overdraw
							- 原理：GPU线程计算

						- 平衡寄存器数量与变体

							- 使用if变量减少变体数量
							- SRP Batch更高效

						- 避免if分支
						- 减少复杂函数

							- 特殊计算单元数量少于正常计算单元

			- Command Buffer和URP

				- 注意

					- 传送门

						- 实现思路

							- 扰动
							- command buffer

								- 前背景？

				- Command Buffer

					- 概念

						- 渲染命令列表缓冲区

					- 应用

						- 抓屏
						- 自定义SRP

					- 其他

						- MaterialPropertyBlock
						- RenderStateBlock

					- 常用函数

						- RenderTexture

							- 中间缓冲区或纹理
							- 应用：后处理
							- 丢失与解决

								- 情况

									- load new Scene
									- 屏幕进行保护模式
									- 全屏进出

								- 解决

									- isCreate检测，重新创建

							- 主动释放

								- RenderTexture.GetTemporary()
								- commanBuffer.GetTemporartRT()

									- 自动remove但为防止bug主动release

						- DrawMesh

							- DrawMesh
							- DrawMeshInstance
							- DrawMeshInstanceProcedural
							- DrawMeshInstanceIndirect

								- 视锥体裁剪的四叉树地形
								- 草地

							- DrawProcedural
							- DrawProceduralIndirect
							- Blit

					- DeBug

						- Scene窗口CameraColorTexture丢失

							- 检查MSAA开关后的RenderTarget绑定情况

								- 自动ResolveAA掩盖Game视窗Bug
								- RenderTarget设置不当

							- 减少使用SetRenderTarget
							- 后处理全屏MeshGame正常而Scene全黑

						- DepthBuffer和StencilBuffer

							- 16bit和24/32bit
							- 申请RebderTexture时，24/32bit的RT会额外连带StencilBuffer

				- URP

					- RenderFeature

						- CustomRenderFeature.cs->CustomRenderPass
						- OnCameraSetup
						- Excute
						- OnCameraCleanUp

					- PostProcessPass

						- 自定义后处理
						- 减少Blit次数
						- Volumn

					- RenderTexture精度格式问题

						- HDR->LDR
						- 精度下降
						- Dither

					- 加速优化

						- 降采样

							- Store/Load Action

						- MSAA

							- 减少RT切换
							- 减少Resolve

						- URP尽量不使用RenderFeature插入Pass

				- 注意

					- 抓帧软件

						- Iphone

							- Xcode

						- Android

					- 抗锯齿AA

						- 大部分采样：TAA>MSAA

							- MSAA不支持延迟渲染
							- TAA闪烁问题

						- FXAA>SMAA在实际测试下出现诸多问题
						- FXAA>SMAA>TAA>MSAA>SSAA

							- SSAA性能消耗太高问题

			- Blend mode

				- Blend

					- finalColor=SrcColor*SrcFactor 
(op) DstColr*DstFactor
					- 操作时机
					- 硬件支持问题
					- Pass内外问题
					- Blend与OpenGL混合兼容问题

				- Ps
				- GrabPass独立混合

			- 剔除

				- 法线剔除 Cull Front/Back/Off
				- 面 Clip();

					- 默认alpha=0.5

				- 问题

					- 双面渲染问题
					- clip函数在PowerVR上的效率问题
					- Clip最好使用AlphaTest队列

		- 四、后处理

			- Bloom

				- 建议

					- 一般开启HDR
					- 高斯模糊
					- BloomMask

				- 原理

					- 提取高亮部分
					- 高斯模糊

						- 高斯核计算
						- 二维计算

					- 原图混合

				- 应用

					- 自发光
					- 特效
					- Gold Ray

						- bloom+镜像模糊

					- ToneMapping

			- SSAO

				- 原理

					- 深度、法线缓冲

						- 深度反推像素世界坐标
						- 法线反推法向半球向量
						- 随机多次采样法向半球计算坐标
						- 获取随机后深度进行比较
						- 加权AO与后期（模糊）

				- 消耗

					- 深度图、法线图采样

				- 特点

					- 近景更明显

				- HBAO

					- 移动端
					- 计算量小

				- GTAO

					- 移动端
					- 计算量小

				- 注意

					- 对比表配图

			- 实时阴影

				- 基于图片的实时阴影技术

					- unity实现

						- projector组件
						- RT阴影映射图
						- 材质设置与阴影映射图混合

					- 原理：GAMES101、GAMES202
					- 阴影映射 Shadow Mao

						- 动态生成（视光源为摄像机的）shadow图与camera的深度图比较

				- 阴影映射优化

					- Z-Fighting 自阴影/阴影瑕疵

						- 解决

							- Bias

								- 原理

									- 容错阈值

								- 深度偏移

									- 新问题：PeterPanning

										- 阴影与投影物脱节

									- 增加偏移使得像素向光源靠近

								- 法线偏移

									- 沿着法线方向向外偏移

							- 增大分辨率

								- 一般不现实

					- 走样

						- 解决

							- 减少远近平面举例
							- 级联阴影映射 Cascaded Shadow map

								- 在远近平面间在划分出“子远近平面”

					- 重采样误差

						- 解决

							- 使用滤波器获得阴影采样点附近区域的输出值

								- PCF滤波
								- 设置阴影的FilterMode

					- 其他技术

						- VSM

				- 注意

					- 场景阴影交互
					- 角色高质量阴影

			- 抗锯齿

				- 官方/图程实现
				- 方案

					- MSAA
					- SSAA
					- TempralAA 时间抗锯齿

						- MSAA每个采样点分时间进行
						- 只保留motion vector

					- FXAA 快速抗锯齿

						- 后期
						- 方法

							- 卷积描边
							- 模糊

				- 移动平台

					- MSAA

				- 对比

					- 效果
					- 效率

						- FXAA>TAA>MSAA>SSAA

				- 注意

					- 瓶颈测试

			- 景深 Dof

				- 概念

					- 摄像：远/近焦
					- 作用

						- 选择性提升某部分清晰度

				- 移动端实现

					- 原理

						- 深度图制作mask
						- 混合不同清晰度图片

				- 问题与解决

					- 官方后处理插件实现原理
					- 不同区域不同处理

						- 前景
						- 背景
						- 景深

					- 颜色泄露 color leakage artifact

						- 解决：扩散滤波
						- 前背景颜色扩散到景深区域

					- 模糊不连续缺陷
					- 散景的模拟Bokeh
					- 闪烁问题

						- 旧版本Unity效果中后处理出现的错误值
						- 解决：均值滤波

				- 缺点

					- 前背景问题
					- 版本问题

						- Unity各版本

					- CommandBuffer景深效果问题

						- 没有渲染顺序

					- 透明物体渲染

		- PBR 基于物理的渲染

			- 光线追踪相关

				- 光线追踪 Ray Tracing

					- 解决光栅化物体丢失全局信息问题
					- 路径追踪 Path Tracing

						- 具体的RT方法
						- 考虑到二次反射问题

				- 光线投射 Ray Casting

					- 三维绘制技术
					- Appel
					- Volume

				- 光线步进 Ray Marching

					- 求光线与物体交点的方法

			- PBR

				- 材质

					- 原理

						- 微平面理论
						- 能量守恒

					- BRDF

						- 原理

							- NDF, Normal Distribution Fuction 法线分布函数

								- GGX

							- G:几何遮蔽函数
							- F:菲涅耳方程

						- 迪士尼原则

							- Unity urp D*F*G=D*V

						- 计算

							- 直接光

								- 直接光反射颜色 =  光源颜色 * （漫反射BRDF + 高光反射BRDF） * LdotN

									- 在这里漫反射BRDF没有使用迪士尼BRDF中的漫反射光照模型，使用的是兰伯特BRDF光照模型。

							- 间接光

								- 间接光（GI）= 间接光（GI）漫反射 + 间接光（GI）镜面反射
								- 镜面反射 = irradiance（反射探针或者sh数据）* occlusion * specularTerm处：bilibili
								- 漫反射颜色 = bakedGI（烘焙光照颜色） * occlusion（环境光遮蔽） * diffuse（颜色纹理）

							- 输出颜色 = 自发光颜色 + 光源颜色 * 反射的BRDF系数 * LdotN

					- 注意

						- PBR风格化修改
						- 物体内各部分风格化的搭配

							- 通透度
							- 人物风格化时各部分的区分

						- 物体间风格化的统一
						- 多pass实现不同效果

				- 灯光

					- 辐射度量学
					- 光度学
					- 灯光类型

						- 精确光
						- IES 光域网
						- Sun

					- 灯光参数

				- 相机

					- 对比

						- unity HDRP下相机
						- Unreal较Unity的长处

							- unity需要搭配后处理
							- ue后处理部分被整合到相机

					- 原理

						- 曝光三角形

							- 快门速度
							- 光圈

								- 影响景深

							- 感光度 ISO

								- 胶片颗粒 Grain

						- 数码相机的模拟

					- 概念

						- 曝光
						- 曝光补偿
						- 直方图
						- 焦距
						- 焦长

					- 相机和引擎

						- Sunny-16法则

			- 体渲染基础

				- 应用

					- 光遇
					- 体积云
					- 体积雾
					- 体积光

				- 缺点

					- 层数问题
					- 精度与噪点

				- 优化思路

					- 降采样
					- 降屏占比
					- 计算算法

				- Unreal大气系统

					- Sky Atmosphere 大气散射

						- Rayleigh
						- Mie
						- Ozone

					- Volumetric Cloud 体积云

			- 流体渲染基础

				- 理论

					- 描述方法

						- 拉格朗日

							- 质点模拟
							- 质点位置随时间变化

						- 欧拉

							- 网格模拟
							- 网格相对位置不变

					- 控制方程

						- 欧拉方法
						- 三大守恒定律

				- 实践

					- 思路

						- 基本着色

							- 漫反射
							- 镜面反射
							- 法线贴图
							- 折射
							- 白沫

						- 效果提升

							- 通透感

								- 深度Lut
								- sss

							- 流动表现
							- 水下雾效

					- 渲染流程

						- Foam modulated by wave height
						- sss
						- normal

							- bump map to jitter

						- fresnel term blend between flection and fraction
						- churn

							- simulate a volumetric effect

						- soft shadow

					- 操作

						- LOD

							- 几何

								- 摄像机为中心的
								- 曲面细分

							- 优化

								- 2 lod of shader

									- 浅水

										- 透明
										- 多细节
										- 多计算量

									- 深水

										- 不透明

									- 远近

						- 高光

							- Minimalist Cook-Torrance

								- 
								- 

							- URP

								- incline InitializeBRDFData()
								- DirectBRDF()

						- 反射

							- NdotV

								- fresnel term blend between flection and fraction

							- 扰动

								- 法线贴图

						- 折射、焦散

							- 焦散
							- The Intensity if the Sun Disk Versus the Angle of Incidence
							- GPU Gems

						- 白沫 Foam

							- 浪尖
							- 岸边

								- 1

									- 白沫mask

										- 场景深度
										- 水深度

									- 白沫贴图

								- 2

									- bump map

										- rgb3层稀疏度

									- ramp

							- GPU Gems 2

						- sss

							- BSSRDF
							- 深度lut
							- 快速sss

								- EA: Direct and Translucey Lighting Vectors

					- Photon Mapping

			- 毛发渲染

				- 长毛

					- e.g.

						- 头发
						- 较长兽毛

					- 插片方式渲染

						- 偏写实毛发走向
						- 体积形态

					- 方法

						- DCC工具制作

							- UV平展

								- 共用一张头发纹理
								- 摆放不同形态不同密度的头发贴图
								- 好处：识别发梢发根，制作变色

							- 流向图

								- 各向异性高光的流向方向信息
								- 特殊结构发型：非写实的体块发型
								- e.g. 阴阳师

						- 技巧

							- GDC2014
							- 献花不透，再画半透背面，最后画半透正面
							- 减小半透排序问题

						- 高光

							- 各向异性高光

								- kajiya-kay算法

							- 叠二层高光

								- 基于经验

							- 细节补充

								- 增加高光流向扰动图
								- AO

				- 短毛/绒毛

					- 基于多层的渲染

						- 多pass

					- 重点

						- 密度
						- 数量
						- 蓬松软质感

					- 问题

						- 移动端性能

					- 特性

						- 透光性

							- 缝隙
							- 穿过毛的表层，向后照亮
							- 外层越稀疏，越容易透光
							- 增加柔软感

						- AO

							- 越往根部，AO越大
							- 高光、轮廓光、边缘散射

						- 毛发走向、各向异性高光

							- 走向

								- 法线方向
								- 自定义：流向图

							- 各向异性

								- 流向图

						- 其他

							- 重力、风力
							- 绒布类材质边缘散射
							- 毛发长短
							- Blendshape动态修改法线方向

					- 改进方向

						- 性能优化：减少渲染层数
						- 毛色变化：发梢发根
						- 丰富交互：移动旋转，惯性模拟
						- 法线效果：增加毛发明暗变化丰富度
						- 抗锯齿：优化边缘

				- 问题

					- 半透排序问题解决方案

						- 高级方案

							- OIT
							- Eye Trick

						- 不用半透明的方案
						- 半透方案

							- prepass写深度
							- 模型层级
							- 渲染次序

				- 制作技巧

					- 逐对象排序

						- 将模型的不同半透层拆分出来
						- 渲染次序基于包围盒中心

							- 非轴心
							- 中心位置一样时难以确定排序次序

					- 面片顺序附加法

						- 创建顶点ID的顺序
						- Detach-Attach

					- 自定义渲染次序

						- 不同面片单位

					- 面片穿插问题
					- 双面渲染
					- 投影问题

						- 投射半透投影
						- 接受投影
						- 原理：深度问题

					- 其他

						- 深色毛发不容易暴漏
						- 模型局部拆分，借助逐对象中心排序

							- 头发刘海拆分
							- 马尾拆分

						- 减少透明部分比例

							- 外层单独使用透明材质
							- 内层使用不透明仅裁剪

						- 使用逻辑修改顶点排序

							- 改变优化半透渲染先后顺序

						- 软化裁剪边缘

							- AlphaTest  +  Alpha To Coverage{Opengl ES 3.0) +  MSAA

### 渲染流水线

- 应用阶段

	- 粗粒度(遮挡)剔除 -> 渲染数据准备 -> 渲染的设置

- 几何阶段

	- 定点函数 -> 曲面细分函数 -> 几何函数 -> 视锥体裁剪 -> MVP变换

- 光栅化

	- 渲染三角形的设置和遍历 -> AA -> 片元函数(三大测试、颜色混合) -> 后处理

### 渲染方式

- forward
- defered

### batch

- 动态
- 静态
- GPU Instancing
-  SRP Batcher

### 空间转换

- MVP变换

	- 变换顺序

		- 缩放->旋转->平移
		- Z->X->Y

	- 变换矩阵

- 法线贴图

	- 模型空间

		- 表现

			- 五颜六色

	- 切线空间

		- 好处

			- 不同模型的复用
			- 压缩

		- 存储相对法线信息
		- TBN矩阵
		- 表现

			- 篇蓝

### AA

### 三大测试

- 透明测试

	- 裁减

		- 性能好：对顶点的敏感度比像素低

	- 混合

- 模板测试
- 深度测试

### Animation

- UV flow

### 光照模型

- 标准经验光照模型

	- diffuse

		- formula

			- 
			- fixed3 diffuse = _LightColor0.rgb * _Diffuse.rgb * saturate(dot(worldNormal, worldLightDir));

		- factor

			- lambert
			- half-lambert

	- specular

		- formula

			-  fixed3 reflectDir = normalize(reflect(-worldLightDir, worldNormal));
			-         fixed3 viewDir = normalize(_WorldSpaceCameraPos.xyz - i.worldPos);
			-         fixed3 specular = _LightColor0.rgb * _Specular.rgb * pow(saturate(dot(reflectDir, viewDir)), _Gloss);

		- factor

			- phong
			- Bling-phong

				-         fixed3 specular = _LightColor0.rgb * _Specular.rgb * pow(saturate(dot(halfDir, normalDir)), _Gloss);

		- Fresnel

	- emission
	- ambient

- 全局光照

	- 蒙特卡洛积分
	- 渲染方程

		- 半球反射问题

			- N=1

		- 光线弹射递归

			- 俄罗斯轮盘赌

- Matcap
- PBR

	- 原理

		- 次表面散射
		- 能量守恒
		- BRDF

	- BRDF

		- NDF
		- Fresnel
		- Geometry

	- 贴图

		- BaseMap
		- NormalMap
		- Metallic+Roughness
		- AO
		- Emission

- NPR-卡渲

	- RampTex

### Shadow

- cascade

### 烘焙

### 后处理

- EdgeDetection
- GaussianBlur

	- 卷积
	- e.g.

		- Bloom

- AO

## 实际方案

### 多地形混合

- 地形

	- 雨水混合

		- 高度图
		- 多贴图Mask融合

	- 交互

		- Unity脚本实时绘制Mask
		- 曲面细分->网格变换

	- 接缝

- 水面

	- 深度
	- uv flow

- 植被

### 描边

- 法线外扩

	- 法线

- mask+边缘检测

	- 模板或深度mask
	- 卷积

- SDF

### 镜面

- 摄像机
- PBR
- 烘焙

	- Cubemap
	- reflect probe

- 屏幕

### 雾玻璃

- 高斯模糊
- flowmap

### 阴影

- 烘焙阴影

### 毛发

- 模型硬毛
- LOD

### 布料

- e.g.

	- cloth
	- Magica Cloth
	- Dynamic Bone
	- Unity Chan / Spring

### 皮肤

### 水墨风

