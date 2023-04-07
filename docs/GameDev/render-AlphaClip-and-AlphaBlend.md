---
title: 透明
layout: doc
date:   2023-04-05 17:27:00 +0800
categories: unity3d, AlphaClip, AlphaBlend, render, Graphic
---


# AlphaBlend 透明度混合
## 原理
 透明面片堆叠

---
# AlphaClip 透明度裁剪
## 优势
 性能消耗相对于AlphaBlend不超过1个量级： 10倍  
 原因：GPU对顶点的敏感度没有drawcall高