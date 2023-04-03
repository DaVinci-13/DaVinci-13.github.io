---
title: Script Coding
layout: doc
permalink: /script/
---


# Scripting

## Language

### C++

- Primer C++

	- C++基础

		- 变量与基本类型

			- 基本内置类型

				- arithmetric type 算术类型

					- 整型

						- 字符
						- bool

					- 浮点型

						- 单精度
						- 双精度
						- 扩展

					- unsigned 无符号类型

				- void 空类型
				- convert 类型转换

					- ps

						- 避免无法预知和依赖实验环境的行为

							- 编译器优势不能检测错误也能正常运行

						- 切勿混用带符号和无符号性

					- undefined 未定义

						- 带符号类型赋值超出表示范围

					- 无符号型表达式

				- literal 字面值常量

			- variable 变量

				- definition 定义

					- object 对象
					- type specifer 类型说明符
					- value 值
					- initialized 初始化

						- list initialization 列表初始化

							- 花括号初始化变量
							- C++11新特性

						- default initialized 默认初始化
						- uninitialized 不被初始化

							- 函数体内部的内置类型变量

				- declaration 声明
				- identifier 标识符

					- 命名规范
					- 关键字

				- scope 作用域

					- 嵌套

						- inner scope 内层作用域
						- outer scope 外层作用域
						- theory

							- 函数体内外

			- compound type 复合类型

				- reference 引用

					- other

						- rvalue reference 右值引用

					- theory

						- lvalue reference 左值引用
						- 别名

					- &

				- pointer 指针

					- theory

						- * 解引用
						- & 取地址
						- 必须初始化

					- 初始化

						- int *p;

					- nullptr 空指针

						- NULL

							- preprocessor variable 预处理变量

					- 无效指针
					- 操作

						- ==/!=

							- 判断存放地址值

					- void* 指针

						- 存放任意对象地址

					- ** 指向指针的指针

						- int **pp=*p;

					- *& 指向指针的引用

						- int *&r=p;

			- const

				- introduce

					- 初始化
					- extern

						- 多文件共享const对象

				- reference to const 常量引用

					- 不能直接修改绑定对象
					- 引用及对应对象都是常量

				- pointer to const 常量指针
				- top-level const顶层const

					- 任意对象为常量

						- int * const p1=&i;

					- low-level const 底层常量

						- 指针指向的对象是常量
						- const int *p2=&i;

					- 拷贝

						- 拷贝时对象必须有相同的底层const资格
						- 或者两个对象的数据类型必须能转换

							- 非常量可以转换成常量

				- const expression 常量表达式

					- constexpr变量

						- C++11新特性
						- 编译器验证变量是否为常量表达式

			- 处理类型

				- type alias 类型别名

					- typedef
					- alias declaration 别名声明

						- C++11
						- using SI=Sales_Item；

				- auto

					- C++11
					- 编译器通过初始值推算变量类型
					- e.g.

						- auto i=42;

				- decltype

					- C++11
					- 选择并返回操作数(结果)的数据类型
					- e.g.

						- decltype(f()) sum=x;

					- ps

						- decltype((i)) d;

							- 双括号结果必为引用

			- 自定义数据类型

				- data member 数据成员

					- in-class initializer 类内初始值

						- C++11

				- 头文件

					- preprocessor 预处理器

						- header guard 头文件保护符

							- 预处理变量

								- #define
								- #ifdef
								- #ifndef
								- #endif

							- 防止重复包含
							- 无视作用域

		- STL, class template

			- using与namespace

				- 头文件不应包含using
				- e.g.

					- std::cin
					- using std;
					- using std::cin;

			- std::string

				- 初始化

					- 直接初始化

						- string s4(10,'c');
						- string s4("ccccccccccc");

					- copy initialization 拷贝初始化

						- string s4="cccccccccc";

				- 读写

					- 读

						- getline

				- empty()
				- size()

					- 返回string::size_type

						- 无符号整型

					- 字符串长度

				- 比较

					- ==/!=

						- 字符串长度相等并包含字符全都相同

					- <\<=\>\>=

						- 字典顺序比较
						- 大小写敏感

				- ps

					- 字符串字面值不是string对象

						- 历史原因
						- 与C兼容

				- 遍历

					- for(auto c:str)
					- for(auto &c:str)

						- c是引用，直接在原字符串修改

					- for(i=0;i<size(str);i++)

			- std:vector

				- instantiation 实例化

					- vector<int> v;

				- 初始化

					- 列表初始化

						- {}

					- value-initialized 值初始化

						- 指定数量
						- ()

				- push_back()

					- ps

						- 不能使用下标添加元素

				- 遍历

					- for(auto &i:v)
					- for(auto i:v)

			- iterator 迭代器

				- 成员

					- begin
					- end

						- off the end 尾后
						- one past the end 尾元素下一位置

				- 运算

					- ==/!=
					- ++/--

				- e.g.

					- for(auto it=s.begin();it!=s.end();++it)

				- 迭代器类型

					- vector<T>::iterator
					- vector<T>::const_iterator

				- 成员访问

					- 解引用
					- ->

				- ps

					- 限制/失效

						- 不能范围for循环添加元素
						- 可能改变容器容量操作

			- 数组

				- ps

					- 字符数组必须留空间存放空字符
					- 不允许拷贝和赋值

						- 某些编译器的编译器扩展支持数组赋值

				- 遍历
				- 缓冲溢出
				- 指针和数组

					- 指针迭代器
					- 指针运算

						- 位置迭代

					- 解引用与指针运算
					- 下标与指针

				- 与旧代码接口

					- CString

						- strlen(p)
						- strcmp(p1,p2)

							- 比较

						- strcat(p1,p2)

							- 附加

						- strcpy(p1,p2)

							- 拷贝

					- 数组初始化vector

				- 多维数组

					- 初始化
					- 下标引用

						- int *ip[4]

							- 整型指针数组

						- int (*ip)[4]

							- 指向含有4个整数的数组

					- 类型别名简化多为数组的指针

						- typedef int int_array[4]
						- using int_array=int[4]

			- 泛型编程

		- 表达式

			- 基础

				- operand 运算对象

					- order of evaluation 求值顺序
					- 转换

						- promoted 提升

							- 小整数型通常会被提升到大整数类型

				- result 结果
				- expression 表达式
				- operator 运算符

					- unary operator 一元运算符
					- binary operator 二元运算符
					- precedence 优先级
					- associativity 结合律
					- overloaded operator 重载运算符

				- 左值和右值

					- rvalue 右值

						- 一个对象被用作右值时，用的是对象的值（内容）

					- lvalue 左值

						- 左值表达式

							- 求值结果

								- 对象
								- 函数

						- 可以在赋值语句左侧

							- 某些左值不能作为赋值语句的左侧运算对象

								- 常量对象

						- 当对象被用作左值时，用的是对象的身份（内存地址）
						- 用到左值的情况

							- 赋值运算符左侧必须是可修改的左值

								- 非常量

							- 取地址符

								- 作用于左值对象
								- 返回指向该左值对象指针

									- 右值

							- 内置解引用运算符、下标运算符、迭代器解引用运算符、string和vector运算符的求值结果
							- 内置类型和迭代器的递增递减运算符

								- 作用于左值对象
								- 结果为左值

					- theory

						- 需要右值的地方可以用左值替代

				- 优先级和结合律
				- 求值顺序

					- 先求运算符左侧运算对象值

						- &&
						- ||
						- ？：
						- ，

			- 算术运算符

				- 异常

					- 溢出

				- +、-、*、/、%

			- 逻辑和关系运算符

				- &&/||/！

					- short-circuit evaluation 短路求值：当左侧运算对象无法确定表达式结果时才会计算右侧运算对象值

				- </<=/>/>=/==/!=

			- 赋值运算符

				- =
				- +=/-=

			- 递增递减运算符

				- *pbeg++

					- *(pebg++)

						- 把pbeg的值加1，然后返回pbeg的初始值的副本作为求值结果

					- 输出当前值并把指针pbeg向前移动一个元素
					- 简洁可以成为一种美德

				- ++/--

			- 成员访问运算符

				- ->

					- 作用于指针类型的运算对象
					- 结果：左值

				- .

					- 解引用运算符*优先级>点运算符.
					- 成员所属对象是左值，结果是左值；成员所属对象是右值，结果是右值。

			- 条件运算符

				- ？：
				- 输出表达式尽量不使用

					- 若使用加（）
					- 产生意想不到的结果
					- 输出符合满足右结合律，优先级高于条件运算符

			- 位运算符

				- ~
				- <</>>
				- &/^/|

			- sizeof

				- 返回

					- 一条表达式或一个类型名字所占的字节数
					- size_t类型的常量表达式

			- ，
			- 类型转换

				- theory

					- conversion 相互转换

				- implicit conversion 隐式转换

					- arithmetric conversion 算术转换

						- integral promotion 整型提升：小整数类型转换成较大的整数类型
						- 无符号类型运算对象

					- 其他隐式转换

						- 数组转换指针
						- 指针的转换
						- 转换成bool
						- 转换成常量
						- 类类型定义的转换

				- 显示转换

					- cast-name<type>(expression);
命名的强制类型转换

						- static_cast

							- 不包含底层const
							- 不在乎潜在精度损失
							- 较大的算术类型赋值给较小的类型
							- 对编译器无法自动执行的类型转换起作用

								- 找回void*指针：
void* p=&d;
double *dp=static_cast<double*>(p);

						- dynamic_cast

							- 运行时类型识别

						- const_cast

							- 只能改变底层const
							- cast away the const, 去掉const性质

								- 将常量对象转换成非常量的行为
								- 编译器不再阻止对该对象进行写操作

							- 常用场景：重载函数上下文

						- reinterpret_cast

							- 通常为运算对象的位模式提供较低层次上的重新解释
							- e.g.

								- 将int对象重新解释为char对象

									- 可能在运行时导致异常

							- 充满风险

					- 建议：避免强制类型转换

		- 语句

			- 简单语句

				- expression statement 表达式语句

					- 执行表达式并丢弃掉求值结果
					- 输入输出语句

				- null statement 空语句

					- 只有一个单独分号

				- compound statement 复合语句

					- block 块

			- 作用域
			- if statement 条件语句

				- if-else
				- switch

			- 迭代/循环语句

				- for
				- while
				- do-while

			- 跳转语句

				- break
				- continue
				- goto

					- 无条件跳转到同一函数内的另外一条语句
					- labeled statement 带标签语句

						- e.g.

							- end: return;

						- 标识符+":"+语句

					- 不能将程序的控制权从变量的作用域外转移到作用域内
					- 向后跳过一个已经执行的定义是合法的
					- 调回到变量定义之前意味着系统将销毁该变量，然后重新创建它

				- return

			- try语句块与异常处理

				- throw expression
				- try block

					- catch

						- 未能找到匹配的catch子句

							- terminate标准库函数

					- exception safe 异常安全

						- 异常发生期间正确执行了“清理”工作

				- exception class

					- exception

						- exception头文件

					- stdexcept头文件

						- exception

							- what()

								- 返回const char*
								- 提供关于异常的文本信息
								- 内容与异常对象类型有关

						- 运行时错误

							- runtime_error

								- 只有在运行时才能检测出问题

							- range_error

								- 值域范围

							- overflow_error

								- 上溢

							- underflow_error

								- 下溢

						- 逻辑错误

							- logic_error
							- domain_error

								- 参数对应结果值不存在

							- invalid_argument

								- 无效参数

							- length_error

								- 试图创建一个超出该类型最大长度的对象

							- out_of_range

								- 使用一个超出有效范围的值

					- bad_alloc

						- new头文件

					- bac_cast

						- type_info头文件

		- 函数

			- 函数基础

				- base

					- function 函数

						- return type 函数组成
						- parameter 形参：0+
						- 函数名
						- function body 函数体

					- 执行

						- call operator 调用运算符
						- argument 实参
						- calling function 主调函数
						- called function 被调函数

				- 局部对象

					- lifetime 生命周期
					- local variable 局部变量

						- 仅参数作用域可见
						- 隐藏在外层作用域中同名的其他声明中

					- automatic object 自动对象

						- 只存在于块执行期间
						- 块末尾销毁，值变为未定义

					- local static object 局部静态对象

						- 执行路径第一次经过对象定义语句时初始化
						- 程序终止时销毁
						- 局部变量定义为static
						- e.g. 函数计次

				- function prototype 函数声明/函数原型

					- 建议变量在头文件爱你中声明
					- 函数在头文件中声明在源文件中定义

				- separate compilation 分离时编译：把程序分割到几个文件中，每个文件独立编译

			- 参数传递

				- 形参

					- passed by reference 引用传递 / called by reference 传引用调用
					- 使用引用避免拷贝

						- 如果无需改变引用形参的值，最好声明常量引用

					- 使用引用形参返回额外信息

				- 实参

					- passed by value 值传递 / called by value 传值调用

				- const参数

					- 顶层const

						- 实参初始化形参是忽略顶层const
						- 当形参有顶层const时，传给它常量对象或者非常量对象都是可以的

					- 指针和引用形参

						- 底层const

					- 尽量使用常量引用

				- 数组形参

					- 数组

						- 不允许拷贝
						- 使用时转为指针

					- 形参写成类似数组的形式

			- 返回
			- 函数重载
			- 特殊用途语言特性
			- 函数匹配
			- 函数指针

		- 类

	- C++标准库
	- 类设计者的工具
	- 高级主题
	- C++11新特性

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

## CLR

### CLR基础

- CLR的执行模型

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

- .Net Framework --生成、打包、部署和管理应用程序及类型

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

- 共享程序集和强命名程序集

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

- 类型基础

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

	- 基元类型、引用类型、值类型

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

	- 类型和成员基础

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

	- 常量和字段

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

	- 方法

		- 实例构造器和类（引用类型）

			- 在方法元数据表中始终叫.ctor
			- 禁止在构造器中调用虚方法，因为会执行派生类对虚方法的实现
			- 编译器在调用基类构造器前使用简化语法对所有字段进行初始化

		- 实例构造器和结构（值类型）

			- 结构不允许显式定义无参构造
			- 结构不能有实例字段初始值
			- 在控制返回到调用方之前，字段必须全部赋值

		- 类型构造器

### 设计类型

### via C#

