+++
date = '2026-04-05T22:00:00+08:00'
draft = false
title = 'UE5 C++ 脚本常用父类：生命周期、常用属性/函数/委托速览'
categories = ['unreal']
tags = ['cpp', 'beginner', 'lifecycle', 'gameplay', 'architecture']
+++

## 前言

在 UE5 C++ 开发里，“选对父类”几乎决定了脚本的生命周期、可放置位置、初始化时机，以及你能用到哪些系统能力（输入、碰撞、网络复制、UI、动画等）。

这篇文章按“实战常用频率”整理：

1. 常见父类分别适合做什么。
2. 每类对象的核心生命周期顺序。
3. 常用属性、函数和委托（含高频回调）。

> 说明：本文聚焦入门和日常开发高频内容，细节会因引擎版本和项目架构（单机/联机）略有差异。

## 1. UObject：一切反射对象的基础

### 适用场景

- 纯数据对象
- 工具类对象
- 不需要直接出现在场景中的逻辑对象

### 生命周期要点

- `Constructor`：构造默认值。
- `PostInitProperties`：属性初始化后调用。
- `BeginDestroy` / `FinishDestroy`：销毁流程。

### 常用属性/函数

- `GetWorld()`：部分上下文可用，不是所有 `UObject` 都有有效世界。
- `GetOuter()`：获取所属外部对象。
- `IsValid()`（配合对象指针检查）：避免访问失效对象。

### 常见委托

`UObject` 本身没有像 Actor 那样丰富的生命周期委托，但可以参与你自定义的动态委托系统。

## 2. AActor：关卡中最核心的可放置对象

### 适用场景

- 场景实体（可见或不可见）
- 可复制的游戏逻辑载体
- 挂组件、处理交互、触发器、机关等

### 生命周期（常见顺序）

1. `Constructor`
2. `OnConstruction`（编辑器放置或属性变更后触发）
3. `PreInitializeComponents`
4. `PostInitializeComponents`
5. `BeginPlay`
6. `Tick`（启用时每帧）
7. `EndPlay`
8. `Destroyed`

### 常用属性

- `PrimaryActorTick.bCanEverTick`：是否允许 Tick。
- `bReplicates`：是否参与网络复制。
- `NetUpdateFrequency`：网络更新频率。
- `Tags`：对象标签，快速分类检索。

### 常用函数

- `BeginPlay()` / `Tick(float DeltaSeconds)` / `EndPlay()`
- `SetActorLocation()` / `SetActorRotation()` / `SetActorTransform()`
- `Destroy()`
- `HasAuthority()`：联机场景判断服务器权限。
- `GetComponentsByClass()`：运行时检索组件。

### 常见委托

- `OnActorBeginOverlap`
- `OnActorEndOverlap`
- `OnTakeAnyDamage`
- `OnDestroyed`

## 3. APawn 与 ACharacter：可控制角色核心

## 3.1 APawn

### 适用场景

- 可被 Controller 控制的对象
- 载具、飞行器、棋子等不一定是“人形角色”的可控实体

### 生命周期要点

继承 `AActor` 生命周期，同时常见控制链路是：

- `PossessedBy(AController*)`：被服务器控制器占有
- `UnPossessed()`：解除占有
- `SetupPlayerInputComponent()`：绑定输入（常见于玩家 Pawn）

### 常用属性/函数

- `AutoPossessPlayer` / `AutoPossessAI`
- `GetController()` / `GetPawnViewLocation()`
- `AddMovementInput()`

### 常见委托

Pawn 自身内置公开委托较少，项目里通常通过组件或自定义委托广播状态变化。

## 3.2 ACharacter

`ACharacter` 是 `APawn` 的高频子类，内置：

- `CapsuleComponent`
- `CharacterMovementComponent`
- `Mesh`

### 适用场景

- 人形角色
- 需要走跑跳、重力、坡度、网络移动预测

### 生命周期/回调补充

- `Landed(const FHitResult&)`：落地事件
- `Jump()` / `StopJumping()`
- `OnMovementModeChanged()`：移动模式切换

### 常用属性/函数

- `GetCharacterMovement()`
- `bUseControllerRotationYaw`
- `GetMesh()`

### 常见委托（常配合组件）

- 角色受伤/死亡常通过自定义委托或 Ability 系统委托实现
- 角色重叠事件常来自 Capsule 的 `OnComponentBeginOverlap`

## 4. AController / APlayerController / AAIController：控制层

### 适用场景

- 输入转发、相机控制、UI 交互（PlayerController）
- AI 决策与行为树驱动（AIController）

### 生命周期要点

- `BeginPlay`
- `OnPossess(APawn*)`
- `OnUnPossess()`
- `Tick`

### 常用属性/函数

- `GetPawn()` / `SetViewTarget()`
- `APlayerController::GetHUD()`
- `APlayerController::ClientTravel()`
- `AAIController::RunBehaviorTree()`

### 常见委托

- `OnPossessedPawnChanged`（常见于 PlayerController 使用场景）

## 5. UActorComponent 与 USceneComponent：可复用能力模块

## 5.1 UActorComponent

### 适用场景

- 为 Actor 提供可复用能力（属性系统、锁定系统、交互系统等）

### 生命周期（常见）

1. `Constructor`
2. `OnRegister`
3. `InitializeComponent`
4. `BeginPlay`
5. `TickComponent`
6. `EndPlay`
7. `OnUnregister`

### 常用属性/函数

- `PrimaryComponentTick.bCanEverTick`
- `GetOwner()`
- `SetComponentTickEnabled()`

### 常见委托

- 多数委托由具体子类组件提供（例如碰撞组件、生命组件等）

## 5.2 USceneComponent

`USceneComponent` 在 `UActorComponent` 基础上增加了变换层级能力。

### 常用函数

- `SetupAttachment()`
- `AttachToComponent()`
- `GetComponentLocation()`
- `SetRelativeLocation()` / `SetWorldLocation()`

## 6. UPrimitiveComponent（及常见子类）：碰撞与可见性核心

### 常见子类

- `UStaticMeshComponent`
- `USkeletalMeshComponent`
- `UBoxComponent` / `USphereComponent` / `UCapsuleComponent`

### 生命周期要点

继承组件生命周期，运行期高频关注“注册后可参与渲染/碰撞”。

### 常用属性/函数

- `SetCollisionEnabled()`
- `SetGenerateOverlapEvents()`
- `SetSimulatePhysics()`
- `SetVisibility()`

### 常见委托

- `OnComponentBeginOverlap`
- `OnComponentEndOverlap`
- `OnComponentHit`

## 7. UUserWidget：UI 脚本核心基类

### 适用场景

- HUD
- 菜单
- 背包、任务、提示等界面

### 生命周期（常见）

1. `NativeOnInitialized`
2. `NativePreConstruct`
3. `NativeConstruct`
4. `NativeTick`
5. `NativeDestruct`

### 常用属性/函数

- `AddToViewport()` / `RemoveFromParent()`
- `GetOwningPlayer()`
- `BindWidget`（通过 UPROPERTY 绑定蓝图控件）

### 常见委托

- 按钮点击：`OnClicked`
- 复选框：`OnCheckStateChanged`
- 滑条：`OnValueChanged`

## 8. AGameModeBase / AGameStateBase / APlayerState：规则与状态分层

### AGameModeBase

- 服务器侧规则核心（客户端通常拿不到 GameMode）
- 常用函数：`StartPlay()`、`PostLogin(APlayerController*)`

### AGameStateBase

- 用于跨客户端同步的全局对局状态
- 常用：倒计时、回合状态、比赛阶段

### APlayerState

- 玩家层面的可复制状态（分数、队伍、名称等）
- 角色死亡重生后常仍保留 PlayerState

### 生命周期提示

- 联机下要明确“规则在 GameMode，展示/同步在 GameState/PlayerState”。

## 9. 委托速查：最常见三类

### 1) 原生委托（非动态）

- 性能更好
- 不能直接暴露给蓝图

### 2) 动态委托（Dynamic）

- 可被反射系统识别
- 可用于蓝图绑定
- 通常比原生委托开销更高

### 3) 多播委托（Multicast）

- 一次广播多个监听者
- 常用于事件总线式解耦

示例（动态多播声明）：

```cpp
DECLARE_DYNAMIC_MULTICAST_DELEGATE_OneParam(FOnHealthChanged, float, NewHealth);

UPROPERTY(BlueprintAssignable, Category = "Event")
FOnHealthChanged OnHealthChanged;
```

## 10. 新手最容易踩的生命周期问题

- 在 `Constructor` 里访问运行时对象（World、PlayerController）导致空指针。
- 组件还没注册就读碰撞/物理状态，结果和预期不一致。
- 把初始化全部塞进 `BeginPlay`，忽略了 `OnConstruction` 在编辑器下的价值。
- 联机逻辑没区分 Authority，导致客户端和服务器重复执行。
- 在委托解绑上遗漏 `RemoveDynamic` / `RemoveAll`，引发悬空回调。

## 小结

UE5 C++ 常用父类可以粗分为：

- 数据与工具层：`UObject`
- 场景实体层：`AActor`、`APawn`、`ACharacter`
- 控制层：`AController`、`APlayerController`、`AAIController`
- 复用能力层：`UActorComponent`、`USceneComponent`、`UPrimitiveComponent`
- 界面层：`UUserWidget`
- 对局规则与状态层：`AGameModeBase`、`AGameStateBase`、`APlayerState`

掌握这些基类的“职责 + 生命周期 + 常用委托”，基本就能搭建大多数游戏玩法脚本框架。

后续可继续写：

1. UE5 C++ 生命周期时序图（从对象创建到销毁）。
2. 联机场景下 GameMode/GameState/PlayerState 的数据流设计。
3. 角色系统实战：Character + Component + Widget 的解耦范式。
