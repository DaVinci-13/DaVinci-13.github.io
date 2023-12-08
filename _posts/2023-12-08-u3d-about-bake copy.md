---
layout: post
title:  Stereo:VR Shader注视点
date:   2023-12-08 17:15:00 +0800
categories: unity, vr, shader, stereo
---
# Stero
VR中左右眼看到的画面不一致的原因：shader注视点问题。  

Shader开启Stereo注视点的相关代码：

```c

struct Attributes
{
    ...
};
struct Varyings
{
    ...
    UNITY_VERTEX_OUTPUT_STEREO
};
Varyings vert(Attributes IN)
{
    Varyings OUT;
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(OUT);
    ...
    return OUT;
}
half4 frag(Varyings IN)
{
    UNITY_SETUP_STEREO_EYE_INDEX_POST_VERTEX(IN);
    half4 c=IN.color.rgb;
    ...
    return half4(c.rgb,1);
}

```