---
title: Garbage Collect 垃圾回收
layout: doc
date:   2023-04-05 17:27:00 +0800
categories: unity3d, gc, CLR
---

# 垃圾回收

## Glossary
1. GC与CLR
2. 内存泄漏：由于“存在该释放却没有释放的错误引用”，导致回收机制认为目标对垃圾”，以至于不能被回收

---
## 泄漏点
- LINQ
    - 原理：
	    - 复制原数据到开辟新内存空间进行SQL操作
	    - 不改变原容器内存储
    - 优点：多线程存储一致性
- GC消耗：CLR自动进行
- 其他
    - 临时变量
    - String
    - IDispose
    - 弱引用 
	- foreach（已被优化）