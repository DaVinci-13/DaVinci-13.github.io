---
layout: post
title:  场景烘焙相关：Lighting、OC
date:   2023-12-08 15:30:00 +0800
categories: unity, bake, lighting， oc
---
# 光照烘焙 Baked Lightmaps
合理光照贴图数量：6组+-

# Occlusion Culling
合理bake缓存大小：100k+-  
建议：OC Area最好设置在活动区，远处不可交互风景地形等使用LOD代替。  
注意：
1. 运动物体不设置任何static相关属性
2. OC Area边界处需要特殊注意，可能会有不正常的OC情况