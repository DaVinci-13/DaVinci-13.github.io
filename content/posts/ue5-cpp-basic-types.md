+++
date = '2026-04-05T21:00:00+08:00'
draft = false
title = 'UE5 C++ 脚本的基本类型'
categories = ['unreal']
tags = ['cpp', 'beginner', 'reflection', 'best-practice']
+++

## 前言

在 Unreal Engine 5 的 C++ 开发中，除了标准 C++ 类型，还会频繁接触 UE 自己封装的一套类型系统。本文作为入门草稿，先把最常用、最容易混淆的类型梳理清楚。

## 1. 数值与布尔类型

UE5 中可以直接使用标准 C++ 基本类型，但官方代码风格更常见的是固定宽度别名：

- `int8` / `uint8`
- `int16` / `uint16`
- `int32` / `uint32`
- `int64` / `uint64`
- `float`
- `double`
- `bool`

示例：

```cpp
int32 Health = 100;
float MoveSpeed = 600.0f;
bool bIsAlive = true;
```

说明：

- `int32` 在 UE 项目中非常常用，跨平台行为更稳定。
- `uint8` 常用于小范围状态值或位标记。
- 布尔变量通常以 `b` 开头（如 `bIsAlive`），是 UE 常见命名习惯。

## 2. 字符串相关类型

UE 里最常见的文本类型有 3 个：`FString`、`FName`、`FText`。

为什么不建议在 UE5 C++ 脚本里优先用 C++ 原生 `std::string`：

- 与 UE 反射系统和编辑器生态耦合较弱，不能直接享受 `UPROPERTY`、蓝图暴露和常见序列化工作流。
- 与 UE 常用 API 对接时通常还要频繁做类型转换（`std::string` <-> `FString` / `FText`），会增加样板代码和维护成本。
- 本地化场景下，`FText` 有完整的文本管线支持；`std::string` 更适合纯底层逻辑，不适合直接做玩家可见文本。
- UE 社区和官方示例主要围绕 `FString`、`FName`、`FText`，团队协作和排查问题时可读性更高。

### FString

- 可变字符串，适合拼接、调试输出、运行时处理。
- 类似“通用字符串容器”。

```cpp
FString PlayerName = TEXT("DaVinci");
FString Msg = FString::Printf(TEXT("玩家: %s"), *PlayerName);
```

### FName

- 不区分大小写语义（底层做了名称表优化）。
- 适合做标识符、标签、键值名、资源名。
- 频繁比较时通常比 `FString` 更高效。

```cpp
FName SocketName = TEXT("WeaponSocket");
```

### FText

- 面向本地化显示文本（UI 文本优先用它）。
- 需要给玩家看的文本，优先考虑 `FText`。

```cpp
FText DisplayText = FText::FromString(TEXT("开始游戏"));
```

## 3. 常用数学结构体

UE5 提供了大量数学类型，最常见的是：

- `FVector`：三维向量（位置、方向、速度）
- `FRotator`：欧拉角旋转（Pitch/Yaw/Roll）
- `FQuat`：四元数旋转
- `FTransform`：位置 + 旋转 + 缩放组合
- `FColor` / `FLinearColor`：颜色

```cpp
FVector Location(0.0f, 0.0f, 100.0f);
FRotator Rotation(0.0f, 90.0f, 0.0f);
FTransform SpawnTransform(Rotation, Location);
```

## 4. 常用容器类型

UE 有自己的模板容器，最常见是：

- `TArray<T>`：动态数组
- `TMap<Key, Value>`：键值映射
- `TSet<T>`：集合（去重）

为什么不建议在 UE5 C++ 脚本里优先用原生 `std::array` / `std::list` 等容器：

- UE 容器与引擎内存管理、反射和序列化工具链配合更完整，尤其在编辑器可视化、保存和网络同步场景更友好。
- 很多 UE API（例如常见 Gameplay、蓝图桥接、工具函数）默认使用 `TArray`/`TMap`/`TSet`，使用 STL 容器时经常要做中转转换。
- `std::list` 在游戏场景里通常不是高频首选，节点分散会降低缓存命中率；`TArray` 在遍历密集场景里往往更实用。
- UE 项目代码风格通常以 UE 容器为主，统一使用能降低沟通成本并减少“容器混用”带来的 bug 风险。

```cpp
TArray<int32> Scores;
Scores.Add(100);
Scores.Add(200);

TMap<FName, int32> AttrMap;
AttrMap.Add(TEXT("HP"), 100);
AttrMap.Add(TEXT("MP"), 50);
```

## 5. UObject 指针相关类型（入门版）

在 UE5 中，和 UObject 体系交互时，指针类型选择非常重要：

- `TObjectPtr<T>`：UE5 推荐的 UObject 成员引用方式
- `TWeakObjectPtr<T>`：弱引用，不阻止对象被 GC
- `TSoftObjectPtr<T>`：软引用，可延迟加载资源
- 原始指针 `T*`：仍可使用，但要注意生命周期与空指针检查

```cpp
UPROPERTY(EditAnywhere)
TObjectPtr<class UStaticMesh> WeaponMesh;
```

## 6. 与反射系统配合：UPROPERTY / UFUNCTION

如果变量要在编辑器中可见、可序列化、可复制或暴露给蓝图，通常需要 `UPROPERTY`。

```cpp
UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = "Stats")
int32 MaxHealth = 100;
```

常见要点：

- 只写 C++ 变量但不加 `UPROPERTY`，编辑器里通常看不到。
- 需要蓝图访问时，常用 `BlueprintReadWrite` 或 `BlueprintReadOnly`。
- 分类用 `Category`，方便在 Details 面板整理。

## 7. 新手易踩坑

- UI 文本直接用 `FString`：后续本地化成本高，优先 `FText`。
- 把所有标识都用 `FString`：很多场景 `FName` 更合适。
- 忽略空指针检查：尤其在异步加载、对象销毁后访问时。
- 容器里放 UObject 原始指针却不考虑生命周期：容易产生悬空引用。

## 小结

UE5 C++ 的“基本类型”不只是 C++ 原生类型，更包括 UE 的字符串、数学结构体、容器和 UObject 指针体系。掌握这些后，再学习反射系统（`UPROPERTY` / `UFUNCTION`）和内存管理机制，会更容易写出稳定的游戏逻辑代码。

后续可以继续写：

1. UE5 C++ 中 `UPROPERTY` 常用元数据速查。
2. `TObjectPtr`、`TWeakObjectPtr`、`TSoftObjectPtr` 的实战对比。
3. 从蓝图迁移到 C++ 时的类型映射与重构策略。
