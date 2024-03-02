---
title:    UE5-C++-学习笔记
layout:    doc
date:   2024-01-30 10:24:00 +0800
categories:    ue5, C++
---
Unreal Engine 5 C++ Developer:Learn C++ & Make Viedeo Games | Udemy

# Welcome

## Intro & setup /安装

### install

https://www.bilibili.com/video/BV1be41137Kp/?p=13&spm_id_from=pageDriver

### forum and support

## Navigating the Viewport /视野窗口

### interface
- New Project
- Viewport
- Outliner
- Content Browser
- toolbat
	- Setting
		- Engine Scalability Setting

---
### shortcut
- mouse
	- right click : rotate all axis
	- left click : rotate in xz panel
	- mid scroll : move in xy panel
- keyboard
	- wasdqe
- ctrl+c & ctrl+v : copy
- alt & drag : copy


## Actor

### Moving & placing Actors  C++ versus Blueprint
- vs
	- Blueprint Strengths
		- Quick to change
		- Beginner friendly
		- Easy to discover
		- Tailor-made
		- Designer/artist friendly
	- C++ Strenths
		- More concise
		- Industry standard
		- High speed
		- Access all areas
		- Good for bigger projects

- work together

---
### Spawning Actors
- Glossary
	- Spawning
		- Creating an object while playing
	- Transform
		- Location, rotation and scale
	- Return pin
		- Output of a node
- Hook Up The Impulse
	- Hook up the execution pins
	- "Add Impulse" should happen affter spawing
	- Hook up the data pins
	- What should we be adding the impulse to?

---
### Geometry Brushes (BSP)
	- Place Actors
		- Brush Type
			- substract
	- Set Default Map
		- Project Settings->Project->Maps&Modes

---
### Objects and References
- Objects
- Glossary
	- Objects - Collections of data and functionality
	- Actors - Object that can go in a level
	- Component - Objects that can go on an actor
	- Reference - Where to find an object
	- Data Pin - The input or output data for a node
	- Excution Pins - When to run this node
- e.g.
	- GetDisplayName
	- GetTheMass

## help us to help you
- Asking For Help
- Good Questions
	- What have you tried?
	- What did you expect to happen?
	- What actually happen?
	- Be specific:exact error, screenshots, etc.
- Useful Information To Include
	- Steps you're taken
	- Screenshots
	- Full Build logs
	- Editor Log
	- Your project
- Log
	- Engine Log Window
	- project Directory->Saved->Logs
- share
	- Engine Toolbar->File->Zip project

# Warehouse Wreckage

## project setting /项目设置
	- map
		- icon
			- with yellow line
	- level blueprint

## Blueprint Event Graph /事件蓝图
- visual programming
- glossary
	- Event Graph - The canvas for our Blueprint
	- Node - premade functionality
	- String - Programmer speak for text
	- Event - A "when" node
	- Pin - Sockets we can connect up
	- Input Pin - when to run this node
	- Output Pin - what to do after
	- Connection - Wires between pins
- e.g.
	- BeginPlay(Event)->PrintString(Func)

## physics /物理
### Detail->physics
- Simulation Physics
- Enable Gravity
- Mass


## Adding an Impulse /力
- Content Sensitive
	- True means it filters down the nodes available to the ones that use the static mesh component object.
- Force and Impulse
	- Force=Mass*Acceleration
	- Impulse=Mass*Velocity Change
- Add Impulse(Component)
	- Impulse(vector3 value)
	- Vel Change(checkbox)
		- change nowtick speed


## Blueprint Classes and Instances /蓝图类
- Glossary
	- BP_Class
		- Detail->Convert ...
	- linked copy
	- instance


### Data Types
- Can't get a square peg in a round hole
- Glossary
	- Integer
	- Float
	- String
	- Bool
	- Struct
		- An object that is usually small
		- e.g.
			- Transform
	- Objects
		- e.g.
			- Actors
				- Cube
			- Components
				- StaticMeshComponent
		- Collections of data and functionality
	- Data type
		- The "Shape" of your data

## Transformation

### Pawns and Actor Location
	- Player Start (Pawn)
	- Get Player Pawn (Node)
### Control Rotation
	- ActorRotation vs. ControlRotation
		- ActorRotation
			- belong to actor
		- ControlRotation
			- associate with inner camera
			- belong to controller
		- controller control actor
			- Pawn->Use Controller Rotation
### Vector Addition & Multiplication
	- What Are Vectors?
		- Mathematically
			- Direction
			- Size(Magnitude)
		- Programmatically
			- 3 Floats
			- XYZ
	- Addition/Subtraction
	- Multiplication
### Get Forward Actor


## Import Assets
- Windows
- Mac
	- Content Browser->\<select Assets or Folder><right click>->Migrate


## Materials and Lighting /光和材质
- Materials
- Lighting
	- Light Source
	- Skylight

## Actor Component /组件
	- Parent and Child Actor

## Collision Meshes /碰撞
- VIEW MODE
	- Locate: <Viewport> -> <Left-up Corner> -> VIEW MODE
	- modes
		- Lit
		- wireframe
		- Player Collision
- Change Collider
	- Static Mesh Editor
		- toolbat->Collision->Remove Collision
- problem
	- flying through
		- move too fast

## Variables /蓝图变量
- Variables Are Like Boxes
	- Variables help us store, manipulate and refer to  information
	- Each variable
		- has a NAME
		- contains DATA
		- is of a particular TYPE
- My Blueprint
	- Locate
		- Level Blueprint
			- Option->Window->My Blueprint
	- VARIABLES
		- function
			- Get
			- Set
	- subtract
		- Get the ammo value from variable
		- Subtract one from it
		- Store it back in the ammo variable
		- Print the result


## Booleans and Branches /蓝图分支
- Branch
	- Do something or do not, based on a bool
- Booleans
	- What Is A Bool?
		- Bools are types that can store one of two values - true or false
		- They are often used with if statements to decide whether something happens or not
		- Certain nodes return bools
	- A yes or no data tyoe
- Comparison
	- Less than, Greater than, Equal, etc.

---
## Functions
- commet block
	- hotkey
		- C
	- put some node into a block
- What Are Functions?
	- Function execute blocks of blueprint that makes our game do thins.
	- Many node provided are functions.
		- It (node) has a little f symbol in the top left that stands for function
	- But we can create our own too.
	- They allow us to stay organised.
	- And reuse blocks of code.
- How to
	- (Select some nodes)->(Right-click)->Convert to Function
- Good Naming
	- Code is communiction.
	- Measure of code quality = WTHs / Minute
	- Functions should be bert
	- Talk to somebody else!

### Return Types
- Details
	- Outputs
		- DataNode
	- Inputs
		- DataNode

### Pure Function
- Side Effect
	- When a function has an observable effect
- What Is A Pure Function
	- A Function with no side effects
	- Only return values
- Make Function Pure
	- Select and set the checkbox
	- What happen to the execution flow

### Member Fuctions
- Glossary
	- Robecje Oriented Programming - Fuctions live with the data they manipulated.
	- Member functions - A function on a class, always called on an particular instance.
	- Self - A node available in member functions, always points to the current instance.

---
## Loading Levels & Delay Nodes
- Open Level
	- by Name
- Get Current Level Name
- Delay

---
# Obstacle Assault

## Project Setup /项目设置
### 切换默认Map
Settings->Project- Maps&Modes

## Editor and Compiler
- Glossary
    - Source Code - Human readable code (like C++).
    - Binary Executable - Machine readable code.
    - Compiler - Translates from Human to Machine.
    - Source Code Editor - Makes writing code fun.

## Live Coding

## Pseudo /伪代码

- Glossary
    - Pseudocode - Plain language description of the steps in an algorithm.
    - Comments - Code that is ignored by the compiler.
---

## Variables /变量
### UPROPERTY()
1. EditAnywhere
2. Scope
3. VisibleAnywhere

### Local
---

## Operator /运算符
Scope Resolution Operator - (::) 范围解析运算符

## Statements
if

## Calling Functions In C++
### Return Value
- Glossary
    - Expression - Fragment of code that produces a value.
    - Statement - An action to be performed.

### Member Function

---
## Using Structs In C++
- Glossary
    - Constructor - Makes a new struct or class value
    - Operator - Symbols that do something. e.g. +,-,=,*,/

## Class
Blueprint Child Class

---
## C++ Files & Lifetime /生命周期

### BeginPlay()

### Tick(float DeltaTime)

- Game Loop
    - Process Input
    - Update game state
    - Render to display

- Glossary
    - Frame - A single picture in a video
    - Frame rate - How many frames per second.(FPS)
    - Tick - Called every frame.

- DeltaTime

---
## Character Component
### Forcing Character Collisions
现象：character在碰撞时不符合常理（闪烁）
原因：脚本不会检测碰撞
trick：
- 设置Character Movement的**MoveUpdatedComponent**
    1. 设置sweep
    2. 蓝图中同一Tick设置Delta变化，e.g. 先加1后减1
    3. 得到Actor的Rotation并设置在组件上

---
# Crypt Raider

---
## Modular Level Design & Layout
模块化水平设计

### Modular Level Design
模块化关卡设计：三视图

### Modular Level Layout
模块化关卡布局

### Solution:Modular Level Layout
模块化关卡解决方案

---
## Light
灯光
### Light Types
灯光类型：
1. Directional Loght 平行光
2. Point Light 点光源
3. Spot Light 聚光灯
4. Rect Light 区域光
5. Sky Light 天光
捕捉远处静态光线，e.g.天空球,作用类似于光照烘焙。

### Lumen
UE新全局光照引擎  
light bleed/光照出血 *：一些老的材质不支持流明而出现渲染错误或异常。需要修改材质编辑器以解决问题。

### Level Lighting

---
## Character Blueprint

### First Person Character Controller

### Third Person Character Controller

---
## Design Mode 设计模式

### Inheritance 继承
A child class automatically has all the functionalirt of the parent. The child "is a" parent.

### Composition 组合
Class A has an instance of Class B, it can choose to use it's functionality but doesn't have to. Class A "has a“ Class B.

---
## Components

### Actor Component

### Scene Componentt
Actor+Transformaiton

### Component Function
``FindComponentByClass``

---
## Pointer 指针

### The * and &(取址符) Symbols in Context

|Symbol|Code Examples|Context|Syntax|Meaning|
|---|---|---|---|---|
|*|UActor *ActorPtr;|Declaring| UActor * |Point to UActor|
||CopyofActor=*ActorPtr;|Using| *ActorPtr |Contents at ActorPtr|
|&|UActor &ActorRef;|Declaring| UActor & |Reference to UActor|
||ActorAddress=&Actor;|Using| &Actor <br> &ActorRef |Address of Actor or ActorRef|

### ->

---
## References 引用
### Comparing Pointers to References

||Pointers|References|
|---|---|---|
|What is stored|Memory Address|
|Can be re-assigned<br>(to another adddress)|Yes|No|
|Can be null|Yes(use nullptr)|No, must be initialised|
|Accessing contents|*ActorPtr|ActorRef|
|Accessing address|ActorPtr|&ActorRef|
|Changing the address|ActorPtr=&Actor|Not allowed|
|Changing the value|*ActorPtr=Actor|ActorRef=Actor|

### Const References & Out Parameters
常量引用传参不允许在方法内修改参数的值
```cpp
void Function(const float &parm)
{
    //parm=2; //will error
}
```

---
## Compilation Steps
### Standard C++ Compilation Steps
|Step|FileType|Content|
|---|---|---|
|(Original)|.cpp & .h|C++代码+头文件|
|Preprecessor|.i|合并C++代码和头文件|
|Compiler|.obj|二进制代码文件|
|Linker|.exe|可执行程序|

### UE Compilation Steps
|Step|FileType|Content|
|---|---|---|
|Unreal Header Tool|.cpp & .h|UHT代码、C++代码、头文件|
|标准C++编译步骤|... ...|... ...|

### Unreal Header Tool (UHT)
#### Blueprint Callable
蓝图可交互

---
## Math

### FMath::VInterpConstantTo
向量插值

---
## Debug

UE_LOG()  
DrawDebugLine()  
DrawDebugSphere()

---
## Keywords

### Out

---
## UWorld
world可以包含多个level

---
## Input Action Mapping

---
## Raycast

1. trace channel：
	- Line Tracing
	- Shape Tracing

2. Sweap
Geometry Sweeping 
- about api:
    - SweepSingleByChannel
    - FHitResult
    - FCollisonShape

---
## Grab
- about api:
	- UPhysicsHandleComponent*
	- GrabComponentAtLocationWithRotation()
	- SetTargetLocationAndRotation()

---
## Wake Physics Handle
- about apo:
	- WakeAllRigidBodies()

---
## Return Out Parameters
Use References

---
## Overlap Events

1. Understand
Overlap==Unity's Trigger  
Block==Unity's Collider

2. Create The Component
Create By BoxComponent

---
## Constructor
1. UHT
```cpp
UCLASS(ClassGroup=(Custom), meta=(BlueprintSpawnableComponent)) 
```
2. Enable ticking in constuctor  
need reopen editor
```cpp
PrimaryComponentTick.bCanEverTick=true;
```

---
## TArray

e.g. GetOverlappingActors()

---
## Loops
1. while
2. for
3. foreach

---
## Actor Label
1. about api:
	- ActorHasTag()
2. Make The Tag Configurable

---
## Dependency Injection
依赖注入：“I need another object but can't find it myself.”  
通常做法：通过蓝图机制的函数调用来实现。

---
## Casting & Actor Attachment
1. (api): AttachToComponent
2. Cast
3. (api): SetSimulatePhysics

---
## Tag: Add & Remove
Actor->Tags  

---
## Boolean Logical Operators
布尔逻辑运算

---
## Level Polish
PostProcessVolume

---
# ToonTanks

---
## Pawn Class Creation
Choosing a class
|Actor|Pawn|Character|
|Can be placed in the world|Can Be possessedby a Controller|Has Character specific stuff(Character Movement Component, etc.)|
|Can have a visual representation(Mesh, etc.)|Handles movement input|Movement nodes(flying)|
||Actor类的基类|适合人形角色|

---
## Components
1. USenceComponet
	- Has a transform
	- Suppots attrachment
	- No visual representation
2. UCapsuleComponent
	- Handles collision
3. UStaticMeshComponent
	- Visual represtation
4. RootComponet

---
## Forward Declaration
前置声明
1. 问题：
	- 头文件互相包含
	- 头文件生成的代码过大
2. 解决的方法：
	- 在.cpp文件中做.h文件的引用
	- .h文件中需要用到该类型时前面加``class``关键字来屏蔽编译错误
3. 其他方法：防止被多次包含``#pragma once``

---
## Constructing The Capsule
创建Note：``CreateDefaultSubobject<*>(TEXT("*"))``  
设置跟组件：``RootComponent=*;``  

---
## Static Mesh Conponent
API：SetupAttachment()

---
## Deriving Blueprint Class

---
## Instance vs Default
1. UPROPERTY Specifers:
	- VisibleAnywhere
	- VisibleInstanceOnly
	- EditAnywhere

---
## Editing Exposed Variables
1. More UPROPERTY Specifers:
	- VisibleDefaultsOnly
	- EditDefaultsOnly
	- EditInstanceOnly
2. Read/Write access in the Event Graph
	- BlueprintReadWrite
	- BlueprintReadOnly

---
## Exposing the Components
1. 允许蓝图访问C++私有变量：`` UPROPERTY(meta=(AllowPrivteAccess="true")) ``
2. `` UPROPERTY(Category="Category Name") ``

---
## Create Child C++ Classes
SpringArm Component  
Camera Component  

---
## Possessing the Pawn
Set **Auto Possess Player** to Player 0

---
## Handling User Input
1. Axis Mapping
2. Binding   
```cpp
void ATank::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
	Super::SetupPlayerInputComponent(PlayerInputComponent);
	PlayerInputComponent->BindAxis(TEXT("MoveForward"),this,&ATank::Move);
}
```

---
## Local Offset
api：AddActorLocalOffset()

---
## Moving Speed
1. Using DeltaTime
	- CPU usage varies
	- Thus DeltaTime varies
	- More frames/second, more function calls!
2. Getting DeltaTiem
```cpp
 UGameplayStatics::GetWorldDeltaSeconds(this);
```

## Local Rotation
旋转：
```cpp
 AddActorLocalRotation(Rotation, bSweep);
```
bSweep: 布尔值，只对根组件RootComponent的Block值为true时有效。

## Cast
类型转换--Casting：
- Template function
- Adapts to the type chosen
- Pass in the type to cast to

## Using The Mouse Cursor
鼠标指针指向的World Location：通过射线实现
```cpp
FHitResult hit;
PlayerControllerRef->GetHitResultUnderCursor(
    ECollisionChannel::ECC_Visibility,
    false,
    hit
);
```

## Rotating the Turret
1. FVector::Rotation()

2. FRotator
- Pitch
- Yaw
- Roll

## The Tower Class
获取1号玩家的Pawn
```cpp
UGameplayStatics::GetPlayerPawn(this,0);
```  
两点间距离：
```cpp
FVector::Dist(location1,location2);
```

## Fire
输入事件绑定Action
```cpp
void AClass::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);
    PlayerInputComponent->BindAction(TEXT("Fire"), IE_Pressed, this, &AClass::Function);
}
```

## Timers
定时器
```cpp
FTimerHandle timerHandle;
float delay=2.f;
bool isLoop=true;
GetWorldTimerManager().SetTimer(timerHandle, this, &AClass::Func, delay， isLoop);
```

## The Projectile Class

## Spwaning the Projectile
1. C++代码使用蓝图类——TSubclassOf
- Template
- Requires a type parameter
- Stores a UClass
    - Subclass of the chosen type
    - Even Blueprints based on the type
2. C++生成actor——Spawning Actors
```cpp
UPROPERTY(EditDefaultsOnly, Category="Combat")
TSubclassOf<AProjectile> template;
UWorld::SpawnActor<AProjectile>(template, location, rotation);
```

## Projectile Movement
1. 投射物移动组件：UProjectileMovementComponnet
- MaxSpeed
- InitilaSpeed

## Hit Events
碰撞事件委托
```cpp
UFUNCTION()
void OnHit(UPrimitiveComponent* HitComp, AActor* OtherActor, UPrimitiveComponent* OtherComp, FVector NormalImpulse, const FHitResult& Hit);

void AClass::BeginPlay()
{
    UStaticMeshComponent* mesh=CreateDefaultSubobject<UStaticMeshCompnent>("Static Mesh");
    mesh->OnComponentHit.AddDynamic(this, &AClass::OnHit);
}

void AClass::OnHit(UPrimitiveComponent* HitComp, AActor* OtherActor, UPrimitiveComponent* OtherComp, FVector NormalImpulse, const FHitResult& Hit);
{
}
```

## Health Component
1. OnTakeAnyDamage Delegate——受伤委托
```cpp
UFUNCTION()
void DamageTaken(AActor* DamagedAction, float Damage, const UDamageType* DamageType, class AController* Instigater, AActor* DamageCauser);

void AClasee::BeginPlay()
{
    GetOwner()->OnTakeANyDamage.AddDynamic(this, &AClass::DamageTaken);
}

void DamageTaken(AActor* DamagedAction, float Damage, const UDamageType* DamageType, class AController* Instigater, AActor* DamageCauser)
{
}
```

## Applying Damage
制造伤害
```cpp
UGameplayStatics::ApplyDamage(actor, demage, GetOwner()->GetInstigatorController(), this, UDamageType::StaticClass());
```

## The Game Mode Class
1. The Game Mode
- Set the default Pawn class
- Handle death
- Starting/ending the game
2. GameModeBase

## Handle Actor Death
获取GmaeMode  
```cpp
AGameMode* AGameMode=Cast<AGameMode>(UGameplayStatics::GetGameMode(this));
```

## Custom Player Controller
1. 启/禁用输入
```cpp
GetPawn()->EnableInput(this);
GetPawn()->DisableInput(this);
```
2. 获取PlayerController
```cpp
APlayerController * aPC=Cast<APlayerController>(UGameplayStatics::GetPlayerController(this,0));
```

## Starting the Game
定时器
```cpp
FTimerHandle playerEnableTimerHandle;
FTimerDelegate playerEnableTimerDelegate=FTimerDelegate::CreateUObject(aPlayerController, &APlayerController::AFunc, true);
GetWorldTimerManager().SetTimer(playerEnableTimerHandle, playerEnableTimerDelegate, delay, false);
```

## The Start Game Widget
1. UI->Widget
2. WidgetBlueprint
    1. Create WBP Coolness Widget
    2. Add to Viewport

## Countdown Timer
1. WBP>Event Graph
2. WBP>"Switch" node

## Displaying Countdown Time

## Winning And Losing
获得某一（C++或蓝图）类的全部演员
```cpp
TArray<AActor*> actors;UGameplayStatics::GetAllActorsOfClass(this, AClass::StaticClass(), actors);
```

## GameOver HUD
1. WBP>"Create WBP End Game Widget Widget"
2. WBP>"Select" node

## Hit Particles 击中粒子效果
生成粒子效果系统
```cpp
UParticleSystem* HitParticle;
UGameplayStatics::SpawnEmitterAtLocation(this, HitParticle, location, rotation);
```

## Smoke Trail 烟雾轨迹
粒子系统与粒子效果组件
|UParticleSystem|UParticleSystemComponent|
|---|---|
|Not a componnent|Is a component|
|Created with `` SpawnEmitterAtLocation ``|Created with `` CreateDefaultSubobject ``|
||Attached to the root|
||Has a Template variable|

## Death Particle

## Sounds
播放声音
```cpp
UPROPERTY(EditAnywhere)
USoundBase* launchSound;
void AClass::BeginPlay()
{
    UGameplayStatics::PlaySoundAtLocation(this, launchSound, location);
}
```

## Camera Shake 镜头摇晃
1. Create a BP based on "CameraShake" Class
2. 使用镜头摇晃
```cpp
UPROPERTY(EditAnywhere)
UCameraShake* CameraShake;
void AClass::BeginPlay()
{
    GetWorld()->GetFirstPlayerController()->ClientPlayCameraShake(CameraShake);
}
```
## Polish And Wrap-Up
1. 相机平滑：BP>Camera Lag

# Simple Shooter
## Section Intro

## Project Setup

## Pawn vs Character
Pawn和Character的区别：
- Character is a Pawn.
- Adds character-like features
- Movement
- NavMesh movement

## Character Movement Functions
Character类下的特性：
- AddMovementInput() 移动
- AddControllerPitchInput() 左右旋转
- AddControllerYawInput() 上下俯仰， 注意需要参考DeltaTime因子                                  
- Jump() 跳

## Controller Aiming

## Third Person Camera Spring Arm

## Skeletal Animations 骨骼动画

## Editing Collision Meshes 编辑碰撞网格

## Animation Blueprint

## 2D Blend Spaces

## Coonnecting Animation To Gameplay

## Inverse Transforming Vectors

## Calculating Animation Speeds
根据动画文件的两步间的时间和位移

## Gun Actor

## Spawning Actors At Runtime

## Attaching To Meshes Via Sockets
1. 根据骨骼名隐藏网格
```cpp
GetMesh()->HideBoneByName(TEXT("bones"), EPhysBodyOp::PBO_None);
```
2. Skeleton蓝图Add Socket
3. 将Actor连接到Socket
```cpp
actor->AttachToComponent(GetMesh(), FAttachmentTransformRules::KeepRelativeTransform, TEXT("Socket"));
actor->SetupOwner();
```

## Shooting Architecture

## Spawning Particle Effects
生成粒子效果
```cpp
UPROPERTY()
UParticleSystem* particle;
UGameplayStatics::SpawnEmitterAtLoction(this, particle, TEXT("SOCKET"));
```

## Player View Point
玩家视角
```cpp
APawn* OwnerPawn=Cast<APawn>(GetOwner());
AController* OwnerCtl=OwnerPawn->GetController();
FVector location;
FRotator rotation;
OwnerCtl->GetPlayerViewPoint(location, rotation);
DrawDebugCamera(GetWorld(), location, rotation. 90, 2, FColor::Red, true);
```

## Line Trace Bu Channel
LineTraceTestByObjectType vs. LineTraceSingleByChannel
```cpp
FVector location=location;
FVector end=location*rotation.Vector();
DrawDebugPoint(GetWorld, location, 20, FColor::Red, true);
FHitResult hit;
GetWorld()->LineTraceSingleByChannel(hit,location,end,ECollisionChannel::ECC_GameTraceChannel1);
```

## Impact Effects
粒子效果
```cpp
UParticleSystem* effect;
UGameplayStatics::SpawnEmitterAtLocation(GetWorld(), effect, location, (-rotation.Vector()).Rotation());
```

## Dealing Damage To Actors
造成伤害
```cpp
FPointDamageEvent DamageEvent(damageNum, hitResult, direction, nullptr);
actor->TakeDamage(damageNum, DamageEvent, OwnerController, this);
```

## Virtual Method in C++
虚方法

## Overriding TakeDamage

## Blending Animation By Boolean
ABP节点

## Blueprint Pure Nodes
1. 蓝图纯节点，没有执行引脚的节点。
2. `` UFUCTION(BlueprintPure) ``

## Create and Setup an AI controller
1. AI控制器
2. 基类：`` AIController ``

## AI Aiming
设置AI的关注点:``AIController->SetFocus(pawn);``  
```cpp
APawn* PlayerPawn = UGameplayStatics::GetPlayerPawn(GetWorld(),0);
SetFocus(PlayerPawn);
```

## Nav Mesh And AI Movement
1. Nav Mesh自动寻路
	1. 节点：Place Actor>Nav Mesh Bounds Volume
	2. BP组件>PathFollowingComponet
2. AIController::MoveToActor()方法
```cpp
MoveToActor(actor,200);
```
3. 注意：需要NavMesh，MoveTo方法单次生效

## Checking AI Line Of Sight
判断AI视野中是否可以看到某个actor
```cpp
if(LineOfSightTo(pawn))
{
	ClearFocus(EAIFocusPriority::Gameplay);
	StopMovement();
}
```

## BehaviorTrees And Blackboards
1. 行为树BT
```cpp
class UBehaviorTree* AIBehavior;
void AIController::BeginPlay()
{
	RunBehaviorTree(AIBehavior);
}
```
2. 黑板BB
3. 顺序节点：Sequence

## Setting Blackboard Keys In C++
1. 获取黑板
```cpp
GetBlackboardComponent()->SetValueAsVector(TEXT("location"), location);
```

## Behavior Tree Tasks And Sequences
1. Tasks
	- MoveTo
	- Wait

## BT Decoratoes And Selectors
1. 装饰器和选择节点
2. 清除黑板值
```cpp
GetBlackboardComponent()->ClearValue(TEXT("location"));
```

## Custom BTTasks In C++
自定义BT树任务
1. BTTaskNode
2. BTTask_BlackboardBase
```cpp
UBTTask_XXXBlackboradValue::UBTTask_XXXBlackboradValue()
{
	NodeName="XXX Value";
}
```
3. 注意：XXX_Build.cs代码添加``GameplayTasks``模块

## Excuting BTTask
行为树任务生命周期：执行
```cpp
EBTNodeResult::Type UBTTask_XXXBlackboardValue::ExcueteTask(UBehaviorTreeComponent &OwnerComp, uinit NodeMemory)
{
	Supper::ExcuteTask(OwnerComp, NodeMemory);
	OwnerComp.GetBlackboardComponent->ClearValue(GetSelectedBlackboardKey());
	return EBTNodeResult::Succeeded;
}
```

## BTTasks That Use The Pawn
获取AIPawn——UBTTask::GetAIOwner()
- BTTaskNode

## BTServices In C++
行为树任务生命周期：Tick
```cpp
EBTNodeResult::Type UBTTask_XXXBlackboardValue::TickNode(UBehaviorTreeComponent &OwnerComp, uinit NodeMemory, float DeltaSeconds)
{
	Supper::TickNode(OwnerComp, NodeMemory, DeltaSeconds);
}
```

## Ignoring Actors In Line Traces
1. 射线检测时忽略actor
```cpp
FHitResult hit;
FCollisionQueryParams params;
params.AddIgnoredActor(this);
params.AddIgnoredActor(GetOwner());
bool bSuccess=GetWorld()->LineTraceSingleBuChannel(hit, location, end, ECollisionChannel::ECC_Channel1, params);
```
2. 分离控制器：``DetachFromControllerPendingDestroy();``
3. 禁用组件的碰撞特性。
```cpp
DetachFromControllerPendingDestroy();
GetCapsuleComponent()->SetCollisionEnabled(ECollisionEnabled::NoCollison);
```

## Ending The Game
在Character里获取GameMode
```cpp
GetWorld->GetAuthGameMode<AGameModeBase>();
```

## Setting Timers In C++
**注意**：DetachFromControllerPendingDestroy方法执行后就无法使用一些方法。

## Displaying a Lose Screen
C++代码中创建UI实例
```cpp
TSubclassOf<class UUserWidget> widgetClass;
void AClass::BeginPlay()
{
	UUserWidget* loseScreen=CreateWidget(this, widgetClass);
	loseScreen->AddToViewport();
}
```
**注意**：XXX_Build.cs中需要添加**UMG**模块

## Iterating Over Actors
迭代Actor
```cpp
for(AController* ctl : TActorRange<AController>(GetWorld()))
{	
}
```

## Calculating The Win Condition

## Refactoring PullTrigger

## Weapon Sound Effects
在Socket播放声音
```cpp
USoundBase* sound；
UGameplayStatics::SpawnSoundAttached(sound, GetMesh(), TEXT("Socket"));
UGameplayStatics::PlaySoundAtLocation(GetWorld(), sound, location);
```

## Randomized Sound Cues
1. 音效编辑器
2. 路径"Add New>Sounds>Sound Cue"
3. Randomlize节点

## Sound Spatialization
立体音效
- Attenuation Distance
- Attenuation Spatialization

## Crosshairs and HUDs
移除UI：``HUD->RemoveFromViewport();``

## Health Bars
ABP->Componet->XXX Property->Bind

## AimOffsets
ABP节点

## Animation State Machines
动画状态机

## Complex State Machine

## Wrap-up And Chanllenges
1. 背景音/环境音效：“Place Actors>Ambient Sound”