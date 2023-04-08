---
title:    Actor
layout:    doc
date:   2023-04-05 19:09:00 +0800
categories:    ue5, actor, editor
---

# Actor

## Moving & placing Actors  C++ versus Blueprint
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
## Spawning Actors
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
## Geometry Brushes (BSP)
	- Place Actors
		- Brush Type
			- substract
	- Set Default Map
		- Project Settings->Project->Maps&Modes

---
## Objects and References
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
