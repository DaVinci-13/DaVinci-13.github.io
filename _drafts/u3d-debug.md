---
layout: post
title:  "Unity 实践， 问题处理"
date:   2023-07-12 16:33:00 +0800
categories: unity, practice, debug
---



# 某物体的光照效果与其他物体相比不对
0. 同shader、同material参数、同lighting参数的情况下
1. 查light组件的mask
2. 查gameobj的layer
3. 查urp setting： Lighting有关（重点Additional Light）

# 某物体移动出某区域自动消失的原因：
0. 查代码
1. LOD有关
2. 剔除有关：注意Static属性的Occluder和Occludee		 