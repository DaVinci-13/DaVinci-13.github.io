---
layout:    doc
title:    the debug of unity environment reflection
date:   2023-10-12 10:22:00 +0800
categories: unity, lighting, environment, reflection
---

# unity中天空球动态加载后环境光照还原问题

## 问题
Unity引擎内部bug，天空球动态加载后，环境反射没有刷新，沿用上一个环境反射

## 处理
动态加载环境反射贴图