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
	- Content Browser-><select Assets or Folder><right click>->Migrate


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
