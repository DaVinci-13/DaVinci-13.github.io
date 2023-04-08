---
layout: doc
title:  "Odin - 学习1"
date:   2023-04-05 14:25:00 +0800
categories: Unity, Odin, Editor
---

# Odin

## Editor

1. 功能
	- FilePath
	- Button
		- ButtonSizes
		- GUIColor
	- ShowInInspector/HideInInspector
	- PreviewField
	- HideLabel
	- LabelText
	- progressbar
2. 辅助
	- Required
	- AssetsOnly
	- PropertyOrder
	- ListDrawerSettings
		- CustomAddFunction 
		- CustomRemoveIndexFunction 

3. Group
	- HorizontalGroup
	- VerticalGroup
	- TabGroup(group, name)
	- TableList
		- TableColumnWidth
		- 
4. Meta
	- ValidateInput( FuncName )
	- OnValueChanged( FuncName )
	- InfoBox( Msg, FuncName)

5. Expression
	- 功能
		- InfoBox
		- ShowIf
	- 特性
		- @
		- $value
		- [#]
6. State
	- OnStateUpdate
	- PropertyRange
	- custom states
		- InspectorProperty.State.Get()
		- InspectorProperty.State.Set() 
7. Space
	- Space
	- PropertySpace
	
---
## OdinEditorWindow
1. Create
	- MenuItem
	- private static void OpenWindow()
	
	```csharp
		- GetWindow&lt;MyCustomEditorWindow&gt;().Show();
		- GetWindow<OdinEditorClassName>().Show();    
    ```
2. Attribute
	- EnumToggleButtons
	- FolderPath
		- RequireExistingPath 
	- InlineEditor
3. Override Function
	- Initialize()
	- GetTarget()
	- BuildMenuTree()
		- Attribute
			- tree.Selection.SupportsMultiSelect
			- tree.DefaultMenuStyle
		- Func
			- Add(name, object)
				- object
					- GeneralDrawerConfig.Instance
			- AddAllAssetsAtPath(name, path, typeof(ScriptableObject))
			- EnumerateTree().AddThumbnailIcons();
4. Serializable