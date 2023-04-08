---
layout:    doc
title:    xLua
date:   2023-04-05 17:47:00 +0800
categories:    Unity3d, light, lightmap
---
# lua热更新

## lua
1. 原理
	- lua运行时才编译的特性: DOT
	- lua文件也可以被看成是一种资源文件
2. 虚拟机
	- 虚拟栈
	- 虚拟机指借助软件系统对物理机器指令执行进行的一种模拟
	- lua脚本并不是直接被Lua解释器解释执行，而是类似Java语言那样，先由Lua编译器编译为字节码，然后再交给Lua虚拟机执行

## xlua
1. 交互
	- [Hotfix]
		- 然后在所有可能出现问题的类上打上HOTFIX的标签，在所有Lua调用的方法上打上LuaCallCSharp标签，在所有CSharp调用Lua的方法上打上CSharpCallLua
	- [CSharpCallLua] 
		- 映射Lua中的变量函数等成C#类型
		- 在C#中对应的Delegate或Interface添加该标签
	- [LuaCallCSharp] 
		- 适配器代码
			- lua虚拟栈
		- 反射
		- xlua.hotfix(CS.类名,‘方法名’,function(self) end) 
2. 具体实现的方法体
- CS.UnityEngine、CS.类名.方法
- self:方法名() 或者 self.方法名(self) 
- CustomCall call=XLuaMgr.GetInstance).Global.Get<CustomCall>"testFun1");
- call();

3. 优势

- 通过[hotfix]对c#中的代码进行修改
	- 可能出现bug或者后期需要更新逻辑
	- 给这个类加上[HotFix]标签，并在方法上打上[LuaCallCSharp]标签，那么当需要更新这个方法时，只需在lua脚本中重新实现这个方法
- GC性能提升
