---
title: Primer C++
layout: doc
date:   2023-04-09 15:20:00 +0800
categories: C++
---

# Primer C++

1. C++基础
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
			- cast-name<type>(expression);命名的强制类型转换

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