---
layout:    doc
title:    热更新
date:    2023-04-06 10：24 +0800
categories:    Unity3d, hot patching
---

# 热更新 Hot Patching

## 流程
	- 打包时放到StreamAssetPath
	- 第一次加载时解压到PersistPath
	- 本地版本号与服务器做对比
	- Hash判断具体AB包需要更新
---

## 脚本热更新方案
