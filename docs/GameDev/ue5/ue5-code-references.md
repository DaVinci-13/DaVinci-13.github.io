---
title:    References
layout:    doc
date:   2023-08-10 10:09:00 +0800
categories:    ue5, code, reference
---

# 引用
## Comparing Pointers to References

||Pointers|References|
|---|---|---|
|What is stored|Memory Address|
|Can be re-assigned<br>(to another adddress)|Yes|No|
|Can be null|Yes(use nullptr)|No, must be initialised|
|Accessing contents|*ActorPtr|ActorRef|
|Accessing address|ActorPtr|&ActorRef|
|Changing the address|ActorPtr=&Actor|Not allowed|
|Changing the value|*ActorPtr=Actor|ActorRef=Actor|

## Const References & Out Parameters
常量引用传参不允许在方法内修改参数的值
```cpp
void Function(const float &parm)
{
    //parm=2; //will error
}
``````