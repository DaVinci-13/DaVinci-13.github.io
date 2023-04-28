---
title: CLR via C#
layout: doc
date:   2023-04-09 15:20:00 +0800
categories: C#, CLR
---

# CLR via C#

## I CLR基础

1. CLR的执行模型
	- 内存管理、加载、编译、安全、异常处理、线程同步
	- 编译：源代码文件->（JIT）编译器->托管模块（IL+元数据）
	- 流程：类库>程序集>托管模块（PE32+头 + CLR头 + IL + 源数据）
	- 通用类型系统CTS,Common Type System
		- 字段+方法+属性+事件
		- 封装：访问修饰符
	- 公共语言规范，CLS，Common Language Specification
	- 与非托管交互
		- 托管代码通过DLL调用非托管函数
		- 托管代码使用非托管COM（Component Object Model）组件（服务器）
		- 非托管代码可以使用托管类型（服务器）

2. .Net Framework --生成、打包、部署和管理应用程序及类型
	- windows应用存在的问题
		- dll hell：一个PE会依赖其他的dll
		- 安装：目录+注册表
		- 安全：悄悄下载
	- 将类型生成到模块中
		- 编译器参考程序集和响应文件将源代码生成PE
		- PE运行时查找响应文件加载程序集
	- 元数据=定义表+引用表+清单表
	- 将模块合并成程序集
		- 调用：CLR->程序集->文件
		- 程序集
			- 可重用（多编程语言实现）类型的基本单元
			- 使用版本号标记，可增量更新
			- 关联安全信息
				- 应用程序通过codeBase指定程序集
				- 将资源与数据文件单独划分
		- 不包含清单表的PE必须加载到另一程序集中使用
	- 程序集版本信息
	- 语言文化
	- 私有部署的程序集
		- PE基目录及子目录
		- 检查防篡改造成性能开销
	- 简单管理控制
		- XML配置文件

3. 共享程序集和强命名程序集
	- 部署与命名
		- 全局部署
			- 公认位置的程序集
	- 强命名程序集
		- 发布者签名，唯一标识
			- 文件名（不计扩展名）+版本号+语言文化+公钥
		- 防篡改
	- 全局程序集缓存，Global Assembly Cache，GAC
	- 延迟签名（delayed signing）/部分签名（partial signing）
		- 开发阶段使用公钥签名生成程序集，之后使CLR暂时信任不做哈希处理，但会失去保护
		- 打包部署使用私钥签名
	- 私有部署强命名程序集
	- 解析
		- 解析路线：CLR->MethodRef->IL->JIT编译->本机代码
		- 解析地址
			- 早期绑定：相同文件
			- 不同文件、相同程序集
			- 不同文件、不同程序集
	- 高级管理控制（配置）
		- 发布者策略控制

## II 设计类型
4. 类型基础
	- Object
		- 最终基类
		- new
			- 创建
				- 计算类型及所有基类型定义字段所需要的字节数
				- 创建管理对象的额外成员
					- 类型对象指针 type object pointer
					- 同步块索引 sync block index
				- 初始化额外成员
				- 调用实例构造器
		- 类型转换
			- 里氏转换
			- 强转
				- is
				- as
		- namespace
		- 运行交互：栈+递归
			- 1个线程分配1MB的栈
			- prologue和epilogue

5. 基元类型、引用类型、值类型
	- 基元类型
		- glossary
			- 直接支持
			- 映射到Framework类库FCL
			- e.g.
				- int=System.Int32
		- 类型转换与溢出检查
			- checked和unchecked
			- CLR的数据转换IL指令
	- glossary
		- 内存必须congo托管堆分配
		- 堆上分配的每个对象必须有类型对象指针和同步索引块
		- 对象中的其他字节总是初始化为0
		- 从托管堆分配对象，内存不足时会强制执行垃圾回收
	- 值类型
		- 具有基元类型的行为，十分简单的类型
		- 无继承关系
		- 类型实例大小
			- 16字节以下
			- 16字节以上但不传参
		- 拆装箱
			- 装箱
				- 在托管堆中分配内存（递归内存+额外成员（类型对象指针+同步索引块））
				- 值类型字段复制到新分配的堆内存
				- 返回对象地址
			- 拆箱
				- 获取已装箱实例的未装箱部分的指针
				- 拆箱之后才紧接着进行内存复制
	- 值类型和引用类型
		- 区别
			- 表示形式：未装箱/已装箱
			- 父类
			- 初始值
			- 传参
			- 拷贝
			- 回收
				- 引用：垃圾回收
				- 值：方法不再活动即被释放
		- 比较：==和equal
		- GetHashcode
	- dynamic基元类型
		- 可用于局部遍历、字段和参数。
		- 在生成IL代码阶段才推断类型
		- dynamic和var的区别
			- var是语法糖，需要编辑器推断类型，并且不兼容表达式

6. 类型和成员基础
	- 成员
		- 常量、字段、实例构造器、类型构造器、方法、操作符重载、转换操作符、属性、事件、类型
	- 可见性
		- 友元程序集
			- [assembly:InternalVisibleTo["**********"]]Internal sealed class XXXType {...}
	- 静态类
		- 必须继承至Ststem.Object
		- 不能实现任何接口
		- 只能定义静态成员
		- 不能作为实例的变量使用
	- 分部类、结构和接口
		- 分部类
			- 源代码控制
			- 在同一个文件中将类或结构分解成不同的逻辑单元
			- 代码拆分
	- 组件、多态和版本控制
		- 组件软件编程，Component Software Programming， CSP
		- 组件的特点
			- .Net Framework：组件=程序集
			- 强命名
			- 程序集的代码永远不会静态链接到另一程序集中：.Net总是使用动态链接（组件永远维护自己的（强命名）标识）
			- 组件必须有引用元数据表
			- 组件必须指定他需要的安全权限
			- 组件要发布任何版本都不会改变的接口
		- 虚方法
			- Call/Callvirt 指令调用
		- 密封类

7. 常量和字段
	- 常量
		- 基元类型
		- C#：非基元类型的null
	- 字段
		- 类型字段的容纳数据需要的动态内存是在内存对象中分配的
		- 类型对象是在类型加载到一个AppDomain时创建的
		- 首次进行JIT编译时才将类型加载到一个AppDomain
		- readonly只能在构造器方法写入
			- 编译器和验证机制
			- 可利用反射修改
			- readonly引用类型时，不可改变的是引用，而不是引用的对象
		- 内联初始化：在代码中直接赋值来初始化，而不是将对构造器的调用写出来


8. 方法
	- 实例构造器和类（引用类型）
		- 在方法元数据表中始终叫.ctor
		- 禁止在构造器中调用虚方法，因为会执行派生类对虚方法的实现
		- 编译器在调用基类构造器前使用简化语法对所有字段进行初始化
	- 实例构造器和结构（值类型）
		- 结构不允许显式定义无参构造
		- 结构不能有实例字段初始值
		- 在控制返回到调用方之前，字段必须全部赋值
	- 类型构造器

9. 参数

10. 属性

11. 事件

12. 泛型
    1. 
    2. 
        1. 
        2. 
        3. 
        4. 代码爆炸
    3. 
    4. 
    5. 
    6. 
    7. 
    8. 可验证性和约束
        约束：where
        无法重写类型参数
        1. 主要约束：0-1
        - class
        - struct
        2. 次要约束：0-？
        - 接口
        - 类型参数约束/裸类型约束：制定的类型实参要么就是约束的类型，要么就是约束的类型的派生类。
        3. 构造器约束：0-1
        4. 其他可验证问题
        - 泛型类型变量的转型
        - 将泛型类型变量设为默认值
            default(T)
        - 将泛型类型变量与null进行比较
        - 两个泛型类型遍历相互比较
        - 泛型类型变量作为操作数使用

13. 接口
    1. 类和接口继承
    2. 定义接口
    3. 继承接口
    4. 关于调用接口方法的更多讨论
    5. 隐式和显示接口方法实现
    6. 泛型接口
    7. 泛型和接口约束
    8. 实现多个具有相同方法名和签名的接口
    9. 用 显式接口方法(EIMI) 实现来增强编译时类型安全性
    10. 谨慎使用显示接口方法实现
    11. 设计：基类还是接口

## III 基本类型
14. 字符、字符串和文本处理
    1. 字符
        - .NET Framework: 16bit Unicode
        - System.Char
    2. System.String  
        不可变（immutable）的顺序字符集，继承于Object
        1. 构造字符串
            - 基元类型
            - Idstr(load string)指令:CLR用一种特殊方式构造字面值String对象
            - unsafe
            - 转义机制
            - GC：
                - 字面值String在编译时连接，最终只有一个字符串放入模块元数据
                - 非字面值String使用 +操作符 ，连接时在运行时进行，在堆上创建多个String对象，需要垃圾会说，对性能有影响
            - 逐字字符串(verbatim string)：引号之间的所有字符会都被视为字符串的一部分
                - @
                - 通常用于制定文件和目录的路径
                - 与正则表达式搭配使用
        2. 字符串是不可变的
            - GC：
                - String类的字符串操作会在对上创建大量的String对象，造成更频繁的垃圾回收，从而影响性能。
                - StringBuilder,高效执行大量字符串操作
            - 不会发生线程同步问题
            - 字符串留用（string interning）：CLR可通过一个String对象共享多个完全一致的String内容，这样能减少系统中的自服从数量，从而节省内存
            - String和CLR紧密集成，出于对性能呢个考虑，String类是密封类
        3. 比较字符串 - 语言文化
        4. 字符串留用
            - 显式调用：String。Interrn
            - 标志
                - System.Runtime.CompilerServices.CompilationRelaxationsAttribute
                - System.Runtime.CompilerServices.CompilationRelaxations.NoStringInterning
            - CLR内部可能对某些字符串进行留用，但不要依赖于CLR的这个行为（CLR版本不同行为不同）
            - 字符串留用虽然有用，但留用本身操作需要花时间，所以使用必须谨慎
        5. 字符串池：编译器只在模块的元数据中的字面值字符串值写入一次。引用该字符串的所有代码都被修改成引用元数据中的统一字符串。
        6. 检查字符串中的字符和文本元素 -  StringInfo
        7. 其他字符串操作
    3. 高效率构造字符串 - StringBuilder
        1. 构造StringBuilder对象
            - 最大容量：Intel.MaxValue
            - 容量：默认16,动态扩容（倍增，复制到新数组，原始数组可以被垃圾回收）
            - 字符数组：
        2. StringBuilder的成员
            - 分配新对象的两种情况：
                - 动态构造字符串其长度超过了设置的容量
                - 调用ToString方法
            - 缺点：不方便、效率低
    4. 获取对象的字符串表示：ToString  
        定义类型时总应该重写ToString方法
        1. 制定具体的格式和语言文化
            - 实现System.IFormattable接口
            - 实现System.IFormatProvider接口
        2. 将多个对象格式化成一个字符串
            e.g. String.Format("On {0:D}, {1} is {2:E} years old.", new DateTime(2012,4,22,14,35,5),"Aidan",9)
        3. 提供定制格式化器
    5. 解析字符串来获取对象： Parse
    6. 编码：字符和字节的相互转换
        1. 字符和字节流的编码和解码
        2. Base-64字符串的编码和解码
    7. 安全字符串 - System.Security.SecureString
        - 字符加密，性能一般
        - 实现了IDisposable接口
        - GC：非托管，回收后内容清0，不再存在于内容中

15. 枚举类型和位标志
    1. 枚举类型
    2. 位标志
    3. 向枚举类型添加方法：扩展方法

16. 数组
    0. 引言
        - CLR支持一维、多维、交错数组。
        - System.Array
        - 引用类型
        - CLS要求所有数组必须是0基数组，但CLR确实支持非0基数组
        - 数组关联了额外开销信息：秩、每一维度的下限、每一维度的长度、数组的元素类型
        - 一维0基数组（SZ数组、向量）性能最佳：可以用一些特殊的IL指令处理
        - 0基以为交错数组的性能和普通向量一样好，不过，访问其元素必须进行两次或更多次的数组访问
        - CLR验证数组索引的有效性：JIT编译器旨在循环开始时检查一次数组边界，不会造成过大的性能损失
    1. 初始化数组
    2. 数组转型
        - Array.Copy()
            - 将元素从一个数组复制到另一个
            - 正确处理内存的层叠区域
            - 进行必要的类型转换
        - 数组协变性（array covariance）：有时确实需要数组congo一种类型转换为另一种类型        
        - 注意
            - System.Buffer.BlockCopy()
                - 只支持基元类型
                - 将按位兼容(bitwise-compatible)的数据从一个数组类型复制到另一个按位兼容的数据类型
            - System.Array.ConstrainedCopy()
                - 可靠地复制数组
                - 未完成复制则抛出异常，不会破坏目标数组中的数据
                - 允许方法在约束执行区(Constrained Execution Region, CER)中执行
                - 源数组和目标数组的元素类型必须相同或者时继承关系
                - 不执行任何装箱、拆箱或向下类型转换
    3. 所有数组的隐式派生自System.Array        
    4. 所有数组的隐式实现IEnumerable, ICollection和IList
    5. 数组的传递和返回
        - 数字作为实参传给方法时，实际传递的时对该数组的引用
        - Array.Copy()执行的是浅拷贝
    6. 创建下限非0的数组
        - Array.CreateInstance()
    7. 数组的内部工作原理
        - CLR内部实际支持两种不同的数组
            - SZ（single-dimensional, zero-based，一维0基、下限为0的一维）数组或向量(vector)
                - e.g. System.String[]
            - 下限未知的一维或多维数组
                - e.g. 
                    - 1基数组 System.String[*]
                    - 多维数组 System.String[,]
        - 访问SZ数组的速度比其他更快：
            - 对于SZ数组有一些特殊指令(newarr, ldelem, ldelema, ldlen, stelem)会导致JIT编辑其生成优化代码
            - for循环的测试表达式对数组的Length属性的调用
            - JIT编译器会生成代码在运行时循环之前进行索引上下限检查
            - CLR允许使用unsafe代码访问数组：在实际访问代码时关闭索引上下限检查
        - 不安全数据访问技术的三处不足：
            - 不易读写：需要fixed语句执行内存地址计算
            - 可能访问到不属于数组的内存：造成计算错误，损坏内存数据，破坏类型安全性，可能造成安全漏洞
            - CLR禁止在降低了安全级别的环境中允许不安全代码
    8. 不安全数组访问和固定大小的数组
        - 避免在堆上分配托管的数组对象：在线程栈上分配数组时通过C#的stackalloc语句完成的：
            - 分配一个内存块，这个内存块可以用不安全的指针来操纵。
            - 栈上分配的内存会在方法返回时自动释放：增强性能。
            - 要使用unsafe
        - 在结构中潜入数组需要满足以下几个条件：
            - 类型必须是结构（值类型）
            - 字段或其定义结构必须用unsafe关键字标记
            - 数组字段必须用fixed关键字标记
            - 数组必须是SZ数组
            - 数组的元素类型必须时基元类型

17. 委托
    1. 引言
        - 非托管C/C++回调函数不是类型安全的：非成员函数的地址知识一个内存地址，不携带任何额外的信息
    2. 用委托回调静态方法
        - 协变性covariance：方法能返回congo委托的返回类型派生的一个类型
        - 逆变性contravariance：方法获取的参数可以是委托的参数类型的基类
    3. 用委托返回实例方法
    4. 委托揭秘
        - 声明委托后，编译器会定义一个派生自FCL定义的System.MulticastDelegate类的一个完整的类
        - 包含构造器、Invoke、BeginInvoke（异步）、EndInvoke（异步）方法
        - 最重要的三个非公共字段：
            - _target:System.Object，静态回调返回null，实例回调返回方法要操作的对象
            - _methodPtr:System.IntPtr，CLR用来标识要回调的方法的整数值
            - _invocationList:System.Object，构造委托链时引用的委托数组
    5. 用委托回调多个方法（委托链）
        - 添加：
        - 删除：每次只会删除委托链从后往前匹配到的第一个委托对象
        - 调用：循环调用委托，完成后返回最后一个委托的结果（其余结果被i舍弃）
        1. C#对委托链的支持：+=、-=
        2. 取得对委托链调用的更多控制
            - 问题：健壮性
            - 解决：new MulticastDelegate().GetInvocationList()
    6. 委托定义不要太多（泛型委托）
        - 泛型委托支持逆变和协变
        - 使用ref、out、params就必须定义自己的委托类型
    7. C#为委托类型提供的简化语法（语法糖）
        - lambda表达式
        - 匿名函数：private static
    8. 委托和反射
        - System.Delegate.MethodInfo.CreateDelegate(Type delegateType)
        - System.Delegate.DynamicInvoke(params Object[] args)

18. 定制特性(custom attribute)  
    定制特性可以宣告式地为代码构造添加**注解**来实现特殊功能。  
    定制特性允许为每一个元数据表记录项定义和应用信息。这种可扩展的元数据信息能在运行时查询，从而动态改变代码的执行方式。
    1. 使用定制特性
        - C#只允许将特性应用于定义以下任何目标元素的源代码：AssemblyDef程序集、ModuleDef模块、TypeDef类型（类、结构、枚举、接口、委托）、FieldDef字段、MethodDef方法（含构造器）、ParamDef方法参数、方法返回值、PropertyDef属性、EventDef事件和泛型类型参数
        - 特性必须前缀明确
        - CLS要求，定制特性类必须直接或间接从公共抽象类System.Attribute派生
        - 定位参数 positional parameter：构造器参数，必须
        - 命名参数 named parameter：字段或属性参数，可选
    2. 定制自己的特性类
        - System.AttributeUsageAttribute 指定特性应用类型
        - 注意:CLR默认定制特性应用于所有目标元素
    3. 特性构造器与字段/属性数据类型
        - 构造器只支持 基元类型 参数，及其SZ数组（会影响与CLS的相容性，应尽量避免）
        - 应用特性时必须传递一个编译时常量表达式，它与特性类定义的类型匹配
            - 在特性类定义了一个Type参数、Type属性或者Type字段的任何地方，都必须使用**C# typeof**操作符
            - 在特性类定义了一个Object参数、Object属性或者Object字段的任何地方，都可以传递Int、String或者常量表达式
            - 若常量表达式代表值类型，则会发生装箱
    4. 检测定制特性
        - 原理：反射
        - 方法：
            - System.Type
            - System.Reflection.CustomAttributeExtensions
                - IsDefined
                - GetCustomAttributes
                - GetCustemAttribute
            - sealed：防止检测到特性类的派生类
    5. 两个特性实例的相互匹配
        - System.Attribute.Equal() 利用反射比较两个特性对象的字段之
        - virtual System.Attribute.Match() 默认为Equal()
    6. 检测定制特性时不创建从Attribute派生的对象
        - System.Reflection.CustomAttributeData() 查找特性时禁止执行特性类的代码
        - 解决了安全隐患：Attribute.GetCustomAttribute会内部调用构造器和可能调用属性的set方法
    7. 条件特性类
        System.Diagnostics.ConditionalAttribute 只有在代码满足编译器条件时（e.g. TEST或Verify 使用代码分析工具）才会在元数据里生成特性信息（造成元数据膨胀，文件变得更大，增大进程的工作及，损害应用程序性能）

19. 可空值类型
    0. 引言
        - CLR的值类型不能为null，会造成一定问题，e.g. 
            - java的Data为引用，而CLR的DataTime为值，在交互时Java可能发送null
            - 数据库的一个列可能为空，则FCL处理就会变得困难
        - 解决：`System.Nullable<T>`
    1. C#对可空值类型的支持
        - 正式写法：Nullable<Iny32>
        - 语法糖:Int32?
        - 支持操作符
        - **注意** 操纵可控实例会生成大量IL代码，速度变慢
    2. C#的空结合操作符： **??**
        - 支持可空值类型和引用类型
        - a==null?a:b
    3. CLR对可空值类型的特殊支持
        1. 装箱
        2. 拆箱
        3. GetType() CLR会“说谎”`Nullabe<T>`的类型是`T`
        4. 接口方法

## IV 核心机制
20. 异常和状态管理
    - 错误处理的步骤：
        - 首先要定义到底什么是错误。
        - 然后要讨论如何判断代码正在经历一个错误，以及如何从错误中恢复。  这个时候，状态就成为一个要考虑的问题，因为错误常常在不恰当的时候发生。代码可能在状态改变的中途发生错误。
        - 当然，还要讨论代码如何同志调用者有错误发送。
    - CLR异常处理：未处理的异常、约束执行区域(constraind execution region, CER)、代码协定、运行时包装的异常以及未捕捉的异常
    
    1. 定义“异常”
        - 异常是指成员没有完成它的名称所宣称的行动。
        - 许多面向对象的构造——构造器、获取和设置属性、添加和删除事件、调用操作符重载和调用转换操作符等——都没办法返回错误代码，但他们仍然需要报告错误。FCL和所有编程语言都通过异常处理来解决这个问题。
    2. 异常处理机制：try{}catch{}finally{}
        - FCL异常处理机制 时用Microsoft Windows提供的结构化异常处理(Structured Exception Handling, SEH)机制构建的。
        - C#另一套异常处理关键字：try{}handle{}compensate{}cleanup{}
        - CLR2.0引入新的RuntimeWrappedException类，将非CLS相容的异常自动构造实例，并初始化该实例的私有字段，使之引用世纪抛出的对象。这样CLR就将非CLS相容的异常转变成了CLS相容的异常。
    3. System.Exception类
        - System.Diagnostics.StrackTrace
        - System.Diagnostics.Debuggabletrribute
    4. FCL定义的异常类
        - 原计划：
            - 基类：Systm.Exception
            - 应用程序抛出异常：System.ApplicationException，自基类派生
            - CLR抛出异常：System.SystemException，自基类派生
        - 规则没有得到严格遵守
    5. 抛出异常
        - 抛出有意义的Exception派生类型，**建议**
            - 强烈建议定义浅而宽的异常类型层次结构，一创建尽量少的基类
            - 谨慎抛出任何基类异常类型
        - 抛出异常时应包含的字符串消息：说明方法为什么无法完成任务
    6. 定义自己的异常类
        - 必须序列化 ``[Serializable]``
    7. 用可靠性换取开发效率
        - 未处理的异常会造成应用程序终止。
        - 而捕捉System.Exception异常并允许应用程序继续运行，一个很大的问题时状态可能遭受破坏。e.g.涉及交易行为
        - 环节对状态的破坏，可以：
            - catch-finaly块中代码CLR不允许线程终止。
            - 用System.Diagnostics.Contracts.Contract向方法应用代码协定。
            - 使用约束执行区域(Constrained Execution Region, CER)消除CLR的某些不确定性
            - 取决于状态存在于何处，可利用事务(transaction)来确保状态要么都修改，要么都不修改。见Systm.Transactions.TransactionScope类。必须P/Invoke（平台调用）本机代码。
            - 将自己的方法设计的更明确：
                - 在线程同步锁的情况下，现在的建议时根本不用随同异常处理使用它们。
                - 如果确定状态已损坏到无法修复的程度，应销毁所有损坏的状态，防止造成根多的伤害，然后重启应用程序，将状态初始化到良好状态，并寄希望于状态不再损坏。
                - 如果状态过于糟糕，应该调用Environment.FialFast()方法终止进程，以不再运行任何的try/finally块或者Finalize方法
    8. 设计规范和最佳实践
        1. 善用finally块
            - 抛出异常后清理已启动的操作
            - 显示释放对象以避免资源泄漏
            - ``lock``.``using``,``foreach``,析构器``Finalize``自动生成try/finally块
        2. 不要什么都捕捉
            - 应该永续异常在调用栈中向上移动，rang应用程序针对性地处理
            - 可在一个线程捕捉异常，在另一个线程中重新抛出异常
        3. 得体地从异常中恢复
        4. 发生不可恢复的异常时回滚部分完成的操作——维持状态
        5. 隐藏实现细节来维系协定
            - 有时需要捕捉一个异常并重新抛出不同的异常
            - 使用``dynamic``基元类型来调用成员，编译器身成的代码就不会捕捉全部异常并抛出一个TargetInvocationException对象：最初抛出的异常对象就会正常地在调用栈中向上传递
    9. 未处理的异常
        - Microsoft建议应用参训开发人员接受CLR的默认策略：发生未处理的异常时，Windows会向事件日志写一条记录
        - Windows查看
            - Windows日志 -> 应用程序
            - Windows操作中心 -> 查看可靠性历史记录
            - Windows操作中心 -> 可靠性监视程序
            - Windows错误报告（Windows Error Reporting）
        - CLR认为本机代码(native code)抛出的异常时损坏状态异常(corrupted state exceptions, CSE)，由于他们一般由CLR自身的bug造成，或者由托管开发人员无法控制的本级代码的bug造成。CLR默认不让托管代码捕获这些异常
    10. 对异常进行调试- Visual Studio设置
    11. 异常处理的性能问题
        - 代价：
            - 非托管编译器会生成大量薄记(bookkeeping)代码：必须生成代码，以跟踪对象被成功构造，以及捕捉到异常时调用已成功构造对象的析构函数。
            - 托管编译器通过GC监视，则生成代码更少
            - 不好判断异常处理到底会使应用程序增大多少额外的开销
        - 必要：异常处理所造成的额外开销，带来的收益远大于对性能的影响
        - 面向对象编程为了提高程序员的编程效率，采取的措施是：不再类型的成员中暴露错误代码
    12. 约束执行区域（CER）
        - CER时必须对错误有适应力的代码块。
        - PrepareConstrainedRegions 提前编译catch和finally代码
        - ReliabilityContractAttribute 特性
        - 保证代码得以执行
            - RuntimeHelper
            - CriticalFinalizerObject
        - **待续**
    13. 代码协定
        - 提供了直接在代码中声明代码设计决策的一种方式
        - 协定采取以下形式
            - 前条件：一般用于对实参进行验证
            - 后条件：方法因为一次普通的返回或者抛出异常而终止时，对状态进行验证
            - 对象不变性(Object Invariant)：在对象的整个生命期内，确保对象的字段的良好状态
        - 核心：System.Diagnostics.Contracts.Contract
        - CCRewrite.exe: 协定的运行工作方式：
            - 前条件协定时方法调用时验证的
            - 后条件协定通过CCRewrite.exe工具时所有返回点在方法返回前执行代码
        - CCChecker.exe:Assert和Assume
            - CCChecker.exe工具可以分析IL代码验证有没有违反协定
            - 有时会由于工具的限制无法验证断言
        - CCRefGen.exe工具：创建一个独立的包含协定的引用程序集
            - 只包含对协定进行描述的元数据和IL
            - 向程序集的定义元数据表应用了System.Diagnostics.Contracts.ContractReferenceAssemblyAttribute
        - CCDocGen.exe:在生成的XML文档中添加协定信息
        - **待续**

21. 托管堆与垃圾回收
    1. 托管堆基础
        0. 引言 
            - 访问一个资源的步骤：
                1. 调用IL指令newobj，为代表资源的类型分配内存。e.g, ``C# new``
                2. 初始化内存，设置资源的初始状态并使资源可用。类型的实例构造器负责设置初始状态。
                3. 访问类型的成员来使用资源（有必要可以重复）。
                4. 摧毁资源的状态以进行清理。
                5. 释放内存。垃圾回收期独自负责这一步。
            - 手动管理资源内存的问题，e.g.原生C++：
                - 内存泄漏：忘记释放不再需要的内存
                - 内存破坏：试图释放已经释放的内存，造成程序错误和安全漏洞
            - 自动管理资源内存的优势：
                - 大多数类型不需要主动摧毁资源的状态以进行清理
                - 对于需要特殊清理的类型（e.g.包装了本机资源：文件、套接子和数据库连接等）时，需要尽快清理资源而不是等GC介入，可调用一个额外的方法**Dispose**按照自己的节奏清理资源
        1. 从托管堆分配资源
            - CLR要求所有对象都从托管堆分配。
                - 进程初始化时，CLR划出一个地址空间区域作为托管堆
                - NextObjPtr：CLR维护一个指针，指向下一个对象在堆中的位置
                - 区域被非垃圾对象填满后，CLR会分配更多区域，直至整个进程地址空间被填满
                    - 32位进程最多分配1.5GB
                    - 64位进程最多分配8TB
            - C# new操作符导致CLR执行以下步骤：
                1. 计算类型的字段（以及从基类继承的字段）所需要的字节数
                2. 加上对象的两个开销字段：
                    - 类型对象指针：32位程序需要32位，增加4字节；64位程序需要64位，增加8字节
                    - 同步索引块：32位程序需要32位，增加4字节；64位程序需要64位，增加8字节
                3. CLR检查区域中是否有分配对象需要的字节数
                    - 若有，则在NextObjPtr指向地址放入对象，接着调用类型构造器（为this参数传递NextObjPtr），new操作符返回对象引用。在返回对象引用之前，NextObjPtr指向下一个位置（当前值加对象占用的字节数）
            - cache miss（缓存未命中）：CLR应用程序能以惊人的速度访问对象，不会被迫凡纳顾问较慢的RAM。在应用程序中，相邻时间分配的对象彼此强关联，而且差不多同一时间访问，因此托管堆在内存中连续分配对象，会因为引用的“局部化(locality)”而获得性能上的提升。进程的工作集会非常小，应用程序只需要很少的内存，从而提高了速度。代码使用的对象可以全部驻留在CPU的缓存中。
        2. 垃圾回收算法
            - 时机：第0代满——在new操作符创建对象时，CLR发现没有足够的地址空间来分配对象。
            - 对象生存期管理：引用跟踪算法/可达性分析
                - 引用计数：不好处理循环引用，e.g.组件对象模型COM。
                - 只关心引用类型的变量（将所有引用类型的变量都称为根）。
            - 过程：
                1. 暂停进程中的所有线程。防止线程在CLR检查过程中访问对象并更改状态
                2. GC的标记阶段：CLR遍历堆中所有对象，将同步索引字段中的一位设位0.这表明所有对象都应删除。
                3. CLR检查所有的活动根，查看他们的引用对象。
                    - 如果一个根包含null，CLR就会跳过这个根并继续检查下个根。
                    - 如果任何根引用了堆上的对象，CLR都会标记这个对象（将同步块索引设为1）。一个对象被标记，CLR会检查这个对象的根并标记他们引用的对象。如果发现对象被标记，就不重新检查对象的字段。
                    - 检查完毕后，堆中的对象要么可达reachable，要么不可达unreachable，可达的对象不能GC
                4. 碎片整理(compact)：移动可达对象到新的连续的内存空间
                    - 恢复引用的“局部化”，减小工作集，提升了性能
                    - 旧的地址空间段永续其他东西进驻
                    - 解决了本机（原生）堆的空间碎片化问题
                5. CLR将每个根减去所引用对象在内存中编译的字节数
            - 如果GC失败，则说明进程内存耗尽，再使用new操作符则会抛出异常
            - 静态对象的内存泄露：静态字段引用的对象会一直存在，指导AppDomain卸载。常见原因时静态字段引用集合对象，然后不停第向集合添加数据向，而所有数据一直存活
        3. 垃圾回收与调试
    2. 代：提升性能
        0. 引言 
            - CLR对代码作出了几点假设：
                - 对象越新，生存期越短
                - 对象越老，生存期越长
                - 回收堆的一部分，速度快于回收整个堆
            - 代的运行机制
                - 初始时分配对象到第0代
                - 一次GC后把幸存者移到第1代，第0代继续接受新对象
                - 第1代不做GC直到预算用完
                - 第1代GC后的新村这放到第2代
            - 托管堆只支持3代：第0代、第1代、第2代
            - CLR的垃圾回收期可以自调节各代的预算： 如果发现第0代幸存者很少则降低第0代预算，增大第1代预算，反之亦然
        1. 垃圾回收触发条件
            - 第0代超过预算
            - 代码显式调用System.GC.Collect()，强制回收第2代
            - Windows报告低内存情况
            - CLR卸载AppDomain
            - CLR关闭
        2. 大对象
            - 目前认为85000字节以上对象位大对象
            - CLR以不同方式对待大小对象：
                - 大对象不再小对象的地址空间分配
                - GC不压缩大对象
                - 大对象总是第2代
            - GC可在很大程度上忽略大对象，直到出现解释不了的情况（e.g.地址空间碎片化）
        3. 垃圾回收模式
            - CLR启动时会选择一个GC模式，在进程终止前不变
            - 两个基本GC模式
                - 工作站：优化点时挂起时间，默认
                - 服务器：优化点时吞吐量和资源利用，多CPU划分托管堆区域并行回收
            - 两个子模式：
                - 并发：默认，倾向于不压缩内存，增强了性能但增大了程序集
                - 非并发
            - GCSettings的GCLatencyMode属性堆垃圾回收进行某种程度的控制：
                - Batch：服务器，关闭并发GC
                - Interactive：工作站，打开并发GC
                - LowLatency：一般用它执行一次短期的、时间敏感的操作，在将模式设回普通。该模式权利避免第2代回收。应避免分配太多对象、大对象，并用一个约束执行区CER将模式设回普通
                - SustainedLowLatency：进程级的设置
        4. 强制垃圾回收 System.GC
            - GC.MaxGeneration
            - GC.Collect():可选择回收几代，回收模式，并发或否
            - 大多数时候应避免调用
            - 防止GC事件过长，使用GC.RegisterForFullGCNotification（和WaitForFullGCApproach,WaitForFullGCComplete,CancelFullGCNotification），应用次序会在垃圾回收器将要执行完全回收时收到通知，以在更恰当的时间强制回收
        5. 监视应用程序的内存使用
            - GC
                - GC.CollectionCount(Int32 generation)某一代发生了多少次垃圾回收
                - GC.GetTotalMemoray(Boolean forceFullCollection)托管堆中的对象当前使用了多少内存
            - PerfMon.exe或者系统监视器ActiveX
            - PerfView
            - SOS Debugging Extension(SOS.dll)
    3. 使用需要特殊清理的类型
        0. 引言
            - 终结(finalization)：CLR允许对象在被判定为垃圾后，但在对象回收之前执行一些代码。
                - 本机资源的终结：CLR判定一个对象不可达时，对象将终结它自己，释放它包装的本机资源。之后，GC会从托管堆回收对象。
                - 避免为引用类型的字段定义可终结对象：可终结对象在回收时存活，造成被提升到另一代，造成了对象活得比正常时间长，增大了内存消耗。更糟的是，可终结对象被提升时，其字段引用的所有对象也会被提升。
            - GC判定对象时垃圾后，会调用对象的Finalize方法。
                - GC完成后才执行Finalize方法
                - CLR不保证多个Finalize方法的执行顺序
                - CLR用一个特殊的、高优先级的专用线程调用Finalize方法避免死锁
                - Finalize方法是为释放本机资源设计的。问题很多，使用须谨慎。强烈建议不要重写。
            - System.Runtime.InteropServices.SafeHandle：封装本级资源的托管类型应该从此类派生。
                - 派生自System.Runtime.ConstrainedExecution.CriticalFinalizerObject.CLR赋予这个类三个功能：
                    - 首次构造该类及派生类对象是，CLR就立即对继承层次结构中的所有Finalize方法进行JIT编译（构造对象时就编译方法），确保该类对象肯定得到释放。否则，内存紧张时，CLR找不到足够的内存编译Finalize方法，方法执行被阻塞，本机资源泄漏。另外，Finalize方法中的代码引用了另一程序及中的类型，但CLR定位该程序集失败，那么资源将得不到释放。
                    - 继承该类的Finalize方法在非继承该类的Finalize方法的调用之后彩绘调用。托管资源类可以在Finalize方法成功访问CriticalFinalizerObject派生类型的对象。e.g.FileStream的Finalize可以放心的将数据从内存缓冲区flush到磁盘，因为磁盘文件此时还没有关闭。
                    - 如果AppDomain被一个宿主应用程序（e.g. Microsoft SQL Server或Microsoft ASP.NET）强行中断，CLR将调用该类的Finalize方法。这个功能确保本级资源得以释放。
                - SafeHandle是抽象类，必须重写其受保护的构造器，抽象方法，抽象方法和抽象属性的get访问器方法。FCL已经集成了SafeHandle的派生类但为公开。
                    - SafeHandle派生类保证本级资源在垃圾回收时得以释放。
                    - SafeHandle派生类在与本级代码交互操作时会获得CLR的特殊对待。
                    - SafeHandle派生类使用引用计数防止有人利用潜在的安全漏洞——句柄循环使用：一个线程可能试图使用一个本机资源，另一个线程试图释放该资源。
                - System.Runtime.InteropServies.CriticalHandle:牺牲安全性换取性能，不用操作计数器
        1. 使用包装了本机资源的类型：实现dispose模式允许使用者控制类所包装的本级资源的生存期
        2. 一个有趣的依赖性问题：FileStream必须在StramWriter后终结，StreamWriter不支持终结
        3. GC为本级资源提供的其他功能
            - 监视内存压力：
                - 原因：本级资源会消耗大量内存，但包装它的托管对象只占用很少内存
                - 解决：GC.AddMemoryPressure(Int64 bytesAllocated)、GC.RemoveMemoryPressure(Int64 bytesAllocated)
            - System.Runtime.InteropServices.HandleCollector：CLR判断进程允许使用的资源数量
        4. 终结的内部原理
            - 表现：创建对象，当其被GC时，调用Finalize()。
            - 条件：``Finalize()``必须被重写
            - 终结列表(finalization list):对象的类型定义Finalize()，则在实例构造器被调用之前，会将指向该对象的指针放入终结列表。
            - ``F-reachable``队列：GC内部数据结构。可终结对象被GC时，会被置入该队列，等待一或多个特殊的高优先级的CLR线程专门调用Finalize(),以避免潜在的线程同步问题。
                - 由于线程多个，所以多个对象的Finalize()调用时机不定。
                - Finalize()中的代码不应该对执行代码的线程做任何假设
                - 需要两次GC：队列中的对象，及引用对象在本次GC时被复活，在Finalize()执行完成后成为真正的垃圾
        5. 手动监视和控制对象的生存期
            - GC句柄表(GC Handle table)：包含对托管堆中的一个对象的引用，以及指出如何监视或控制对象的标志。
            - ``System.Runtime.InteropServices.GCHandle``类
                - 在GC句柄表中添加删除记录项
                - Alloc()传递想控制/监视的对象的引用
                - 传递GCHandleType，制定方式如何控制/监视对象：
                    - Weak：GC可检测GC什么时候判定对象不可达，GC时，将其放入F-reachable队列变为WeakTrackResurrection
                    - WeakTrackResurrection：GC可检测GC什么时候判定对象不可达，Finalize()执行后，回收内存
                    - Normal：即使没有根引用该对象内存也必须留在内存中，可以压缩
                    - Pinned：即使没有根引用该对象内存也必须留在内存中，不可以压缩，e.g.异步IO操作中，字节数组缓存区在内存中不可移动
            - ``fixed``：编译器定义，效果同GCHandle.Pinned
            - ``System.WeakReference<T>``弱引用：
                - 效果同GCHandle.Weak
                - 优点：简便、安全
                - 缺点：实例必须在堆上分配
                - 应用场景：缓存情形
            - ``System.Runtime.CompilerServices.ConditionALWeakTable<TKey,TValue>``:将数据与单独对象关联
            - **待续**

22. CLR寄宿和AppDomain
    0. 引言
        - CLR COM服务器：Windows为CLR定义了一个标准COM接口。
        - 寄宿(hosting)：使现有的应用程序至少能部分使用托管代码编写。还提供了通过编程来进行自定义和扩展的能力。
        - AppDomain:允许第三方的不受信任的代码在现有的进程中运行，而CLR保证数据结构、代码和安全上下文不被滥用和破坏。
        - 寄宿、AppDomaon与程序集的家在和反射经常一起使用
    1. CLR寄宿：
        - CLRCreateInstance():MetaHost.h中声明。MSCorEE.dll中实现            
        - MSCorEE.dll：垫片(shim)。决定创建CLR的版本。见ICLRMetaHost.GetRuntime()，应用程序中的XML配置文件中的requiredRuntime和supportedRuntime.
        - ICLRRuntimeHost:
            - 设置宿主管理器
            - 获取CLR管理器
            - 初始化并启动CLR
            - 加载程序集并执行其中的代码
            - 终止CLR
    2. AppDomain
        - CLR COM服务器初始化时创建AppDomain。AppDomain在进程终止时销毁。
        - AppDomain的功能
            - CLR创建的第一个AppDomain时默认
            - 隔离：一个AppDomain中的代码不能直接访问另一个AppDomain中的代码创建的对象。
                - 即使两个AppDomain加载了同一个程序集的同一类型，他们的Loader堆也会分别分配一个类型对象
                - AppDomain中立：有的程序集可以分配在特殊的Loader堆，由所有AppDomain共享。缺点是只能在Windows进程终止时才能回收资源
            - AppDomain可以卸载：但不能卸载AppDomain中的特定程序集
            - AppDomain可以单独保护
            - AppDomain可以单独配置
        - 跨越AppDomain边界访问对象
            - 机制：
                - 按引用封送(Marshal-by-Reference)
                - 按值封送(Marshal-by-Value)
                - 完全不能封送
            - 租约管理器(lease manager)：非默认Appdomain中的对象默认存活5分钟。5分钟内没有代理调用，则时效；若有，则续约。
            - **待续**
    3. 卸载AppDomain
        - AppDomain.Unload()：
            1. CLR挂起进程中执行国托管代码的所有线程
            2. CLR检查所有的线程栈，若栈上有要写在的AppDomain,CLR会强迫对应的线程抛出一个``ThreadAbortException``（同时恢复线程的执行）。这将导致线程展开(unwind)，并执行遇到的所有finally块一清理资源。如果没有代码捕捉``ThreadAbortException``，CLR将会“吞噬”（当异常没有发生）这个未处理的异常；终止线程，进程继续运行。
            3. CLR遍历堆，在无效的代理对象上设置标志，表示引用其的对象已经不在了。
            4. CLR强制垃圾回收已卸载的AppDomain的任何内存。
            5. 恢复生于线程的执行。
        - 同步
    4. 监视AppDomain——AppDomian.MonitoringEnabled
    5. AppDomain FirstChance异常通知
        异常首次抛出，通知所有FirstChanceException回调，所没有catch处理，则CLR终止线程
    6. 宿主如何使用AppDomain
        **待续**
    7. 高级宿主控制
        1. 使用托管代码管理CLR——System.AppDomainManager
        2. 写健壮的宿主应用程序
            - 得体的终止线程或AppDomain
            - 设置升级策略(escalation policy)告诉CLR如何处理托管代码的错误
        3. 宿主如何拿回它的线程：落跑(runaway)线程问题
            **待续**

23. 程序集加载和反射
    1. 程序集加载
        - 普通加载方式：
            - System.Reflection.Assembly.Load()
            - System.Reflection.Assembly.LoadFrom()
            - System.Reflection.Assembly.LoadFile()
        - 反射分析程序集并禁止代码执行
            - System.Reflection.Assembly.ReflectionOnlyLoad()
            - System.Reflection.Assembly.ReflectionOnlyLoadFrom()
            - 标记程序集以通知CLR不自动加载：
                - AppDomain.ReflectionOnlyAssemblyResolve事件
                - AppDomain.ResolveAssembly事件：引用嵌入EXE内的DLL资源
    2. 使用反射构建动态可扩展应用程序
        - System.Reflection反射元数据表
        - 适用情况：
            - 类库需要理解类型的定义才能提供丰富的功能；
            - 应用程序需要从特定程序集加载特定类型以执行特定任务，e.g.晚期绑定；
    3. 反射的性能
        - 缺点：
            - 编译时无法保证类型安全性；
            - 速度慢。
        - 避免使用反射动态发现和构造类型
            - 让类型从编译时已知的基类型派生；
            - 让类型实现编译时一直的接口。
        1. 发现程序集中定义的类型——new Assembly().ExportedTypes
        2. 类型对象的准确含义
            - 巴克斯-诺尔范式(Backus0NaurForm, BNF)：构造传给反射方法的字符串时，要使用类型名臣或限定了程序集的类型名称。
            - 使用操作符并根据已知的类型名称来获得Type对象。e.g. `` typeof ``
            - `` TypeInfo ``:CLR加载类型定义的程序集以进行解析，可能代价高昂。
        3. 构建Exception派生类型的层次结构
        4. 构造类型的实例
            - System.Activator.CreateInstance():接受Type和String
            - System.Activator.CreateInstanceFrom()：不接受Type
            - new System.AppDomain().CreateInstanceXXX()
            - new System.Reflection.ConstructorInfo().Invoke()
    4. 设计支持加载项的应用程序：程序集的版本控制问题
        **待续**
    5. 使用反射发现类型的成员
        1. 发现类型的成员—— System.Reflection.MemberInfo
        2. 调用类型的成员
            - PropertyInfo
            - EventInfo
            - BindToMemberThenInvokeTheMember
            - BindToMemberCreateDelegateToMemberTherInvokeTheMember
            - UseDynamicToBindAndInvokeMember
        3. 使用绑定句柄减少进程的内存消耗
            - RuntimeTypeHandle
            - RuntimeFiledHandle
            - RuntimeMethodHandle

24. 运行时序列化
    0. 引言
        - 序列化是将对象或对象图转换成字节流的过程。
        - 反序列化是将字节流转换回对象图的过程。
        - 对象图(object graph)是对象系统在特定时间点的一个视图。
        - e.g.
            - 应用程序的状态可以轻松的保存到磁盘文件或数据库，，并在应用程序下次运行时恢复。
            - 克隆一组对象作为“备份”。
            - 通过网络把一组对象从一台机器发送到另一台机器的进程
            - 一次对象可复制到系统的剪贴板，在粘贴会同一个或另一个应用程序。
            - 加密和压缩。
        - 难点：通信协议、客户端/服务器数据类型不匹配（比如低位优先/高位优先问题）、错误处理、一个对象引用了其他对象、in和out参数以及有结构构成的数组等。
    1. 序列化/反序列化快速入门
        - 格式化器：BinaryFormatter、SoapFormatter（生产环境废弃）
        - 注意事项：
            - 序列化和反序列化使用相同的格式化器
            - 序列化时，类型的全名和类型定义的程序集的全名会被写入流。反序列化时，格式化器首先获取程序集标识信息，并通过反序列化方法家在程序集到AppDomain。若字段不完全匹配则抛出异常。
    2. 使类型可序列化——``[Serializable]``特性
        - 应用于引用类型(class)、值类型(struct)、枚举(enum，默认可序列化)、委托(delegate，默认可序列化)
        - 基类不允许序列化，派生类不可序列化
    3. 控制序列化和反序列化
        - ``[NonSerialized]``特性：定制序列化类型中不应序列化的字段。e.g，经序列化后无效的信息（如句柄）；很容易计算的信息（以增强性能）。
        - ``[OnSerializing]``、``[OnSerialized]``、``[OnDeserializing]``、``[OnDeserialized]``特性：序列化和反序列化回调
        - ``[OptionFiled]``：为方便版本控制，可序列化不包含该字段的对象
    4. 格式化器如何序列化类型实例
        - 序列化流程——格式化器使用``FormatterServices``序列化对象：
            1. 调用``FormatterServices.GetSerializableMembers``方法利用反射获取public和private实例字段置入``MemberInfo[]``返回；
            2. ``FormatterServices.GetObjectData()``接收``MemberInfo[]``为参数并返回``Object[]``（MemberInfo数组的值数组，一一对应）；
            3. 格式化器将程序集表示和类型完整名称写入流中；
            4. 遍历``MemberInfo[]``和``Object[]``,将每个成员的名称和值写入流中。
        - 反序列化流程：
            1. 格式化器从流中读取程序集标识和完整类型名称。将程序集加载到AppDomain中，将程序集表示信息和类型全名传给``FormatterServices.GetTypeFromAssembly``，该方法返回一个``System.Type``对象；
            2. 格式化器调用``FormatterServices.GetUninitializedObject()``为对象分配内存但不调用构造器；
            3. 格式化器调用``FormatterServices.GetSerializableMembers()``方法构造并初始化``MemberInfo[]``；
            4. 格式化器根据流中包含的数据创造并初始化``Object[]``；
            5. 将新分配对象、``MemberInfo[]``以及``Object[]``的引用传给``FormatterServices.PopulateObjectMembers()``，将对象的每个字段初始化成对应的值。
    5. 控制序列化/反序列化的数据——``ISerializable``接口
        - 优点：完全控制。
        - 要实现ISerializable但基类没有实现怎么办？手动序列化基类的字段：获取他们的值并添加到SerializationInfo集合中。
    6. 流上下文——``StramingContext``
        通过流上下文标志一不同的方式生疮它的状态，从而深科隆对象图中的所有对象。
    7. 类型序列化为不同类型以及对象反序列化为不同对象
        序列化单例，继承ISerializable接口
    8. 序列化代理 —— ``ISerializationSurrogate``接口
        对于注册了代理的类型的对象进行序列化和反序列化，使用代理对象定义的方法。
    9. 反序列化对象是重写程序集/类型 —— ``SerializationBinder``类
        非常简单的将一个对象反序列化成不同类型。

25. 与WinRT(Window Runtime)组件互操作
    **待续**（win8定义Windows Store应用的开发环境，不常用）

## 线程处理
26. 线程基础
    1. 历史：
        - 职责：（单CPU时期）对CPU进行虚拟化，为进程提供了一个专用的线程
    2. 线程开销
        - 线程组成要素：
            - 线程内核对象(thread kernel object)：数据结构，包含一组对线程进行描述的属性。            
            - 线程环境块(thread environment block, TEB)：
                - 是在用户模式（应用程序代码能快速访问的地址空间）中分配和初始化的内存块。
                - 耗用1个内存页。
                - 包含 异常处理链首、线程本地存储，以及GDI(Graphics Device Interface, 图形设备接口)和部分OpenGL图形数据结构。
            - 用户模式栈(user-mode stack)：
                - 存储方法的局部变量和实参。还包括方法返回后继续运行的地址。
                - 默认分配1MB内存。
            - 内核模式栈(kernel-mode stack)
                - OS内部处理的地址空间。
                - 32位大小时12KB，64位是24KB。
            - DLL线程连接(attach)和线程分离(detach)通知：新创建和销毁线程会通知所有非托管DLL的DLLMain()
        - 上下文切换
            - 步骤：
                1. 将寄存器的值保存在正在运行的线程的内和对象内部的一个上下文结构中；
                2. 从现有线程集合中选出一个线程供调度；
                3. 将所选上下文结构中的值加载道CPU的寄存器中。
            - 量程(量quantum，时间片)，上下文切换的单位，时间片到期则执行时间片切换。Windows大约每30ms执行一次时间片切换。
            - 性能损耗：
            - 速度取决于CPU架构和速度。
            - 尽量避免线程，因为耗用大量内存，而且需要耗时管理。
        - 只有多CPU计算器才能真正允许几个线程。这提升了应用程序的可伸缩性（用更少的时间做更多的工作）。
    3. 停止疯狂
        - 任何机器最优的线程数就是那台机器的CPU数目。
        - Windows侧重于可靠性和响应能力，而非速度与性能。
        - Windows应用程序大都以效率低下的方式使用线程。与进程相比，创建线程十分廉价。但CPU利用率为0%的线程白白占用着内存，纯属浪费。
    4. CPU发展趋势——多核：暂停提升CPU速度，改为将晶体管作的更小
        今天的计算机使用的多CPU技术：多个CPU、超线程芯片、多核芯片
    5. CLR线程和Windows线程——完全等价
    6. 使用专用线程执行异步的计算限制操作
        - 强烈避免使用
        - 创建专用线程:构造System.Threading.Thread类的实例
    7. 使用线程的理由
        - 主要是出于两方面的原因使用线程：可响应性（通常是对于客户端GUI应用程序）、性能（对于客户端和服务器应用程序）
        - PC应该CPU利用率100%进行工作。除非使用电池供电。
        - 数据中心需要在CPU运行和散热维护费用间作平衡。
    8. 线程调度和优先级