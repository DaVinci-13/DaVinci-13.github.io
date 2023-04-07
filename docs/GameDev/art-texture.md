---
title: 贴图资源规范
layout: doc
date:   2023-04-05 19:07:00 +0800
categories: art, texture
---

# 贴图资源规范

## u3d
1. minmap
2. 压缩格式设置
    - ETC
	- HEVC
3. 最大限度利用资源
	- 尽量使用 **正方形纹理**：unity总是把贴图处理成边长为2^n的正方形
	- rgba通道，e.g.
	    - 把 自发光、自遮挡deng贴图压缩到同一个图片文件的不同通道
	    - 按需求导入Alpha通道