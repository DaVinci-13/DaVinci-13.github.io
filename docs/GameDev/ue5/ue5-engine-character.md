---
title:    Character
layout:    doc
date:   2023-07-19 16:51:00 +0800
categories:    ue5, character, code
---

# Forcing Character Collisions
现象：character在碰撞时不符合常理（闪烁）
原因：脚本不会检测碰撞
trick：
- 设置Character Movement的**MoveUpdatedComponent**
    1. 设置sweep
    2. 蓝图中同一Tick设置Delta变化，e.g. 先加1后减1
    3. 得到Actor的Rotation并设置在组件上
