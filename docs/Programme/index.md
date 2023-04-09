---
title: Programming Language
layout: doc
permalink: /programme/
---


# Programming

## Language

### [C++](./cpp.md)


- Unreal C++
- other

	- IO

		- cin
		- cout

			- while(std::cin>>value)

				- 读取数据直到文件尾

	- 控制

		- for
		- while
		- if

	- error错误

		- syntax error 语法错误
		- type error 类型错误
		- declaration error 声明错误

	- 类简介

- CMake
- C++网络

### C#

- Unity C#

	- 委托和事件

		- Func<param, return> 返回值委托
		- Action<param> 无返回值委托
		- 事件

			- 委托的封装
			- 类中的对象
			- 内部调用

		- lambda表达式

			- 匿名委托
			- 实现原理

				- 表达式树

					- 转换为树状结构
					- 只进行存储不进行计算

	- 线程相关

		- Await和Async

			- 线程切换

		- 上下文

	- 模版

		- 泛型

			- 泛型类
			- 泛型方法
			- list<T>和arraylist的区别

				- 装箱拆箱
				- 类型安全

			- 容器

				- List

					- 注意

						- 下标越界
						- 下表前移

				- Dict

					- 遍历

				- 迭代器

		- 类模版
		- where关键字

			- 应用

				- T:struct

					- 类型参数必须为值类型

				- T:class

					- 类型参数必须为引用类型

				- T:new()

					- 类型参数T必须有一个公有、无参的构造函数。当于其它约束联合使用时,new()约束必须放在最后。

				- T:BASE_CLASS_NAME

					- 类型参数必须是指定的基类型或是派生自指定的基类型

				- T:INTERFACE_NAME

					- 类型参数必须是指定的接口或是指定接口的实现。可以指定多个接口约束。接口约束也可以是泛型的

			- T

				- 类型参数

	- 扩展

		- 内联函数和宏

			- incline

				- 将函数调用直接展开为函数体代码

			- #define
			- 减少函数调用的开销

		- local function 本地函数

			- 闭包

		- partial class 部分类
		- LINQ

			- 适用情境：多线程/网络
			- 原理

				- 生成临时对象，最后合并
				- 数据存储一致性
				- 排序稳定性

		- 弱引用

			- 能被GC回收
			- 建立弱引用

				- Object obj = new Object();
				- WeakReference wref = new WeakReference( obj ,bool trackResuttrction=false);

					- trackResuttrction 跟踪复活

				- obj = null;

			- 建立连接则转换成强引用

				- Object obj = wref.Target;

	- 内存模型

		- 编译

			- CLR
			- CIL
			- Mono
			- IL2CPP

		- 托管资源

			- 分配
			- 回收

				- 清空引用，GC回收
				- 时机

					- 内存不足时

			- 与C++不同之处

		- 非托管资源

			- 分配
			- 回收

				- dispose模式

					- 语法糖

						- using()

							- try/finally格式的语法糖
							- finally内会主动调用 Dispose() 

					- 实现IDispose接口
					- 垃圾回收

						- 释放非托管资源
						- 不受CLR管理

				- finalize

					- 有时无法判断何时调用Dispose()

						- 有时候持有非托管资源的变量可能被用在很多地方，我们无法显示判断在何时调用 Dispose() 方法释放该资源

					- 实现Finalize()会通过GC调用

						- 只有在 GC 的时候，我们判断引用该非托管资源的变量已经不被任何其他对象引用
						- GC过程是内部实现的，我们无法在 GC 过程中手动调用 Dispose() 方法

		- 内存泄漏

			- static
			- 分析

				- profiler

	- 多线程

- 其他

	- toplevel statement 顶级语句

		- C# 9.0
		- 不用写Main函数
		- 框架自动生成持续入口文件

	- 测试

		- NUnit框架

			- 框架自动生成持续入口文件

### Lua

- 基本类型

	- nil
	- bool

		- false

			- nil
			- false

	- number
	- string

		- .gsub()

			- 替换

	- table

		- 元表

			- 元方法

				- index
				- new index

					- 时机

						- 使用不存在的Key

			- 原理

				- 目的

					- 两个table之间的操作

				- 操作步骤

					- Lua 查找一个表元素时的规则，其实就是如下 3 个步骤:
					- 1.在表中查找，如果找到，返回该元素，找不到则继续
					- 2.判断该表是否有元表，如果没有元表，返回 nil，有元表则继续。
					- 3.判断元表有没有 __index 方法，如果 __index 方法为 nil，则返回 nil；如果 __index 方法是一个表，则重复 1、2、3；如果 __index 方法是一个函数，则返回该函数的返回值。

		- pair与ipar

			- ipar根据下标遍历，到下标不存在处则停止退出循环

	- function

		- .func()和:func()

			- 使用：会默认传入self指针

	- thread
	- userdata

- 面向对象

	- 封装

		- table+function
		- 元表

	- 继承

		- 子类设置元表为父类
		- 父类元表为自己

	- 多态

		- index设置为函数，从多个父类搜索

- 协程
- 缺点

	- 内存泄漏

		- C#中对象销毁，LUA失去对象

			- LUA指向C#引用，C#引用真正对象

	- 面向对象消耗性能

		- 原理

			- 字符串匹配
			- table->metatable

### ShaderLab

- CG
- HLSL
- 优点

	- 可交互效果

## 数据结构

### String

- 引用类型
- 内存分配模型

	- 临时对象

		- 表现的像值类型
		- 该表一个string的值不会影响到引用了该string其他字符串

### 位运算

- 理论

	- 原码
	- 反码
	- 补码

- 实践

### 内存分配

- Heap堆区

	- 一般由程序员分配释放
	- GC回收
	- 不连续的内存

- Stack栈区

	- 由编译器自动分配释放
	- 系统分配
	- 速度快
	- 溢出

		- 大小固定

	- 存放局部变量

- 静态区

	- 全局变量和静态变量全局变量和静态变量在一块区域， 未初始化的全局变量和未初始化的静态变量在相邻的另的存储是放在一块的，初始化的一块区域
	-  程序结束后由系统释放

- 文字常量区

	- 常量字符串就是放在这里的
	- 程序结束后由系统释放

- 程序代码区

	- 存放函数体的二进制代码

### 虚函数、抽象类和接口

- 抽象类

	- 只继承，不实现
	- 抽象方法
	- 虚函数

- 接口

	- 只有方法界面
	- 实现接口必须实现其中所有方法

### 结构体和类

- 区别

	- 内存位置

		- 值与引用
		- 堆与栈

	- 参数默认访问权限：结构体只能public
	- 继承性：结构体不能继承
	- new操作

		- struct

			- 调用构造函数初始化参数
			- 不能有初始值

	- 构造函数

		- struct

			- 默认无参构造
			- 有参构造必须初始化所有参数

- 值类型和引用类型

	- 栈和堆
	- 最终父类
	- 引用与传参
	- 多态

- 堆和栈

	- 空间大小
	- 释放方式
	- 访问效率
	- 分配

		- 静态增长
		- 动态增长

	- 地址

		- 从低到高
		- 从高到低

### 闭包

- theory

	- 存在自由变量的函数

		- 约束变量
		- 自由变量

### GC

- 原理

	- 引用计数
	- 线性遍历堆内存

- 时机

	- 自动执行
	- 手动调用
	- 内存不足

- 问题

	- 内存碎片化

- 优化

	- 对象池
	- 手动调用GC

### 装箱和拆箱

- 值类型和引用类型的转换
- e.g. ArrayList
- 装箱

	- 堆区开辟内存，将占区对象数据赋值到此处

### 反射

- 反射

	- e.g.

		- Reflect
		- as
		- attribute 注解

			- 注解就是在不破坏原有代码的情况下，在代码的元数据上附加一些信息(一般附加类，而不是附加字符串——明显类能表达的东西更多)。然后工具类在遍历所有类的时候，注意着看看attribute表达给我们的信息就行了——这个方法上有着忽略的attribute，那我就不把他当函数;这个类上有忽略的attribute，我就不把他当数据类;这个属性上有别名的attribute，我就换个名字输出。

		- DllImport

			- 运行dll里的函数

		- MethodImpl(MethodImplOptions.AggressiveInling)

			- 运行时特别优化一下这个函数(内联)

	- 原理

		- MetaData

			- FuncData

				- 类内所有方法的数据表

			- PropData

				- 类内所有属性的数据表

		- C#内部实现

## Algorithm

### 大纲

### leetcode-H

- Subtopic 1

## 软件工程相关

### 面向*

- 面向过程

	- 不支持类和对象
	- C
	- 执行效率优势

- 面向对象

	- C++，C#，Java，PHP
	- 方便组织和管理代码，快速梳理思路，编程思想上的革新

### 设计模式

- 单例模式
- 观察者模式

	- 实现方法

		- 接口
		- 广播

- 工厂模式

	- 简单工厂

		- 一个工厂返回一种产品

	- 工厂方法

		- 抽象基类
		- 一个虚方法
		- 每个具体工厂返回一种产品

	- 抽象工厂

		- 抽象基类 + 接口
		- 多个虚方法
		- 多个具体工厂返回多种产品

- 组合模式

	- ecs

### 架构

- ECS

	- DOTS
	- Entitas

- MVC

	- 解耦合

## [CLR](./cs.md)
