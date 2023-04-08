---
title:    蓝图分支
layout:    doc
date:   2023-04-08 11:16:00 +0800
categories:    ue5, blueprint, function
---


# Functions
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

---
# Return Types
- Details
	- Outputs
		- DataNode
	- Inputs
		- DataNode

---
# Pure Function
- Side Effect
	- When a function has an observable effect
- What Is A Pure Function
	- A Function with no side effects
	- Only return values
- Make Function Pure
	- Select and set the checkbox
	- What happen to the execution flow

---
# Member Fuctions
- Glossary
	- Robecje Oriented Programming - Fuctions live with the data they manipulated.
	- Member functions - A function on a class, always called on an particular instance.
	- Self - A node available in member functions, always points to the current instance.