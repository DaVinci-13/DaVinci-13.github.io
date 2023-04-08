---
title: Unity3d Optimization 性能优化
layout: doc
---
# unity3d 性能优化

## Unity3d Editor特性：
1. 遮挡剔除
2. 精灵图集

## 脚本编写优化
1. 降低代价：
    1. 对象池
    2. Unity Update
        - 固定增量时间
        - 空的事件方法
        - 空的生命周期
        - 循环
    3. API. e.g.
        - gameObject.GetComponment()
        - transform.Find()
        - Camera.main
2. 异步处理
    1. 加载
        - Resources
        - Assetbundle
    2. Corotinue 协程
    3. Async. 原理：多线程
3. 减少复杂计算
    - 减少**坐标系变换**计算：尽量使用transform.tion
    - 注意**数据类型与精度**的选取和使用（变量类型所占内存）